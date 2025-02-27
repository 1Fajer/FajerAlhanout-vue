<template>
  
    <div class="recent-chat-container border-end px-3" style="background-color: white;">
      <div class="list-group-item top-chat">
        <div class="d-flex justify-content-between align-items-center">
          <div class="d-flex align-items-start">
            <div class="avatar-container position-relative me-2">
              <img :src="topChat.avatar" class="rounded-circle avatar" alt="User Avatar" />
              <span class="status-indicator" :class="topChat.status"></span>
            </div>
            <div class="d-flex flex-column">
              <h4 class="mb-1 top-chat-name">{{ topChat.name }}</h4>
              <p class="text-muted fw-lighter mb-2 top-chat-job">{{ topChat.job }}</p>
            </div>
          </div>
          <i class="bi bi-three-dots-vertical dots-menu"></i>
        </div>
        <div class="search-bar">
          <i class="bi bi-search search-icon"></i>
          <input type="text" v-model="searchQuery" class="form-control" placeholder="Search contact" />
        </div>
        <p class="text-muted my-2 toggle-chats" @click="toggleChats">
          Recent Chats
          <i class="bi" :class="showChats ? 'bi-chevron-up' : 'bi-chevron-down'"></i>
        </p>
        <transition name="fade">
          <div v-if="showChats" class="list-group">
            <a v-for="chat in filteredChats" :key="chat.id" href="#" class="list-group-item list-group-item-action" :class="{ 'list-group-item-secondary': chat.active }">
              <div class="d-flex w-100 align-items-center ">
                <div class="avatar-container position-relative">
                  <img :src="chat.avatar" class="rounded-circle avatar" alt="User Avatar" />
                  <span class="status-indicator" :class="chat.status"></span>
                </div>
                <div class="w-100">
                  <div class="d-flex justify-content-between">
                    <h5 class="chat-name">{{ chat.name }}</h5>
                    <small class="chat-time">{{ chat.time }}</small>
                  </div>
                  <p class="chat-message">{{ chat.message }}</p>
                </div>
              </div>
            </a>
          </div>
        </transition>
      </div>
    </div>
  
</template>

<script>
export default {
  data() {
    return {
      showChats: true,
      searchQuery: "",
      topChat: {
        name: "Fajer Saleh",
        job: "Marketing Director",
        avatar: `https://api.dicebear.com/9.x/lorelei/svg?backgroundType=gradientLinear,solid&seed=TopChat`,
        status: "available",
      },
      chats: [
        { id: 1, name: "Alanoud", time: "3 min ago", message: "Hey! How are you?", status: "available", active: true },
        { id: 2, name: "Bedour", time: "2 hrs ago", message: "Are you free tomorrow?", status: "busy", active: false },
        { id: 3, name: "Amirah", time: "5 hrs ago", message: "Let's catch up this weekend!", status: "idle", active: false },
        { id: 4, name: "Maryam", time: "1 day ago", message: "I sent you the notes.", status: "available", active: false },
        { id: 5, name: "Salamh", time: "2 days ago", message: "Did you watch the new episode?", status: "busy", active: false },
        { id: 6, name: "Faten", time: "3 days ago", message: "Thanks for the help yesterday!", status: "idle", active: false },
      ],
    };
  },
  computed: {
    chatsWithAvatars() {
      return this.chats.map(chat => ({
        ...chat,
        avatar: `https://api.dicebear.com/9.x/lorelei/svg?backgroundType=gradientLinear,solid&seed=${encodeURIComponent(chat.name)}`,
      }));
    },
    filteredChats() {
      return this.chatsWithAvatars.filter(chat =>
        chat.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    toggleChats() {
      this.showChats = !this.showChats;
    },
  },
};
</script>

<style scoped>


.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.recent-chat-container {
  width: 100%;
  max-width: 100%;
  padding: 0.7rem;
  box-sizing: border-box;
  overflow: hidden;
  font-size: 0.85rem;
  background: white;
}

.top-chat {
  font-weight: bold;
  cursor: pointer;
  padding: 0.8rem;
  max-width: 100%;
  width: 100%;

}

.avatar-container {
  position: relative;
  display: flex;
  align-items: center;
}

.avatar {
  width: 2.2rem;
  height: 2.2rem;
  border-radius: 50%;
}

.status-indicator {
  position: absolute;
  bottom: 0.2rem;
  right: 0.2rem;
  width: 0.6rem;
  height: 0.6rem;
  border-radius: 50%;
  border: 1px solid white;
}

.available { background-color: green; }
.busy { background-color: red; }
.idle { background-color: yellow; }

.top-chat-name {
  font-size: 0.85rem;
}
.top-chat-job {
  font-size: 0.75rem;
}

.dots-menu {
  font-size: 1rem;
  cursor: pointer;
}

.search-bar {
  display: flex;
  align-items: center;
  background: white;
  border-radius: 0.3rem;
  border: 1px solid #ccc;
  padding: 0.3rem;
}

.search-icon {
  font-size: 1rem;
  color: gray;
  margin-right: 0.5rem;
}

.search-bar input {
  border: none;
  outline: none;
  width: 100%;
  font-size: 0.85rem;
}

.toggle-chats {
  font-size: 0.85rem;
  cursor: pointer;
}

.list-group-item {
  padding: 0.7rem;
  font-size: 0.85rem;
}

.chat-name {
  font-size: 0.8rem;
}
.chat-time {
  font-size: 0.7rem;
  color: gray;
  font-weight: normal;
}
.chat-message {
  font-size: 0.7rem;
  font-weight: normal;
  color: #555;
}
</style>
