<template>
  <div class="recent-chat-container border-end bg-white position-relative">
    <div class="top-chat">
      <div class="d-flex justify-content-between align-items-center">
        <div class="d-flex align-items-start mt-3 mx-3">
          <div class="avatar-container position-relative me-2">
            <img :src="topChat.avatar" class="rounded-circle avatar" alt="User Avatar" />
            <span class="status-indicator" :class="topChat.status"></span>
          </div>
          <div class="d-flex flex-column mb-2 px-1">
            <h6 class="mb-1 fw-semibold top-chat-name" style="font-size:normal;">{{ topChat.name }}</h6>
            <small class="text-muted top-chat-job" style="font-size:x-small;">{{ topChat.job }}</small>
          </div>
        </div>
        <i class="bi bi-three-dots-vertical dots-menu text-dark pe-2 "></i>
      </div>
      <!-- Search Bar with Icon Inside -->
      <div class="d-flex justify-content-between align-items-center px-3 position-relative border rounded mx-4  mt-3">
        <input
          v-model="searchQuery"
          type="text"
          class="form-control form-control-sm border-0 pe-5"
          placeholder="Search contacts"
          aria-label="Search contacts"
        />
        <i class="bi bi-search"></i>
      </div>
      
      <!-- Modified Recent Chats Toggle -->
      <div class="d-flex align-items-center px-3 pt-5 position-relative">
        <p class="text-muted toggle-chats m-0 me-2" style="font-size: small;">
          Recent Chats
        </p>
        <p class="toggle-chats m-0" @click="toggleSortMenu">
          <i class="bi" :class="showSortMenu ? 'bi-chevron-up' : 'bi-chevron-down'"></i>
        </p>
        
        <!-- Sort Menu -->
        <transition name="fade">
          <div v-if="showSortMenu" class="sort-menu position-absolute">
            <button class="btn btn-sm btn-light text-muted" @click="handleSort('name')">Sort by Name</button>
            <button class="btn btn-sm btn-light text-muted" @click="handleSort('date')">Sort by Date</button>
            <button class="btn btn-sm btn-light text-muted" @click="handleSort('unread')">Mark All Unread</button>
          </div>
        </transition>
      </div>
      
      <transition name="fade">
        <div>
          <div v-for="chat in filteredChats" :key="chat.id" class="py-1 d-flex align-items-center">
            <div class="avatar-container position-relative mx-3">
              <img :src="chat.avatar" class="rounded-circle avatar" alt="User Avatar" />
              <span class="status-indicator" :class="chat.status"></span>
            </div>
            <div class="flex-grow-1 my-2">
              <div class="d-flex justify-content-between">
                <small class="me-1 fw-semibold" style="font-size:small;">{{ chat.name }}</small>
                <p class="text-muted" style="font-size: xx-small; padding-right:4%;">{{ chat.time }}</p>
              </div>
              <small class="text-muted d-block" style="font-size:x-small;">{{ chat.message }}</small>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showSortMenu: false,
      searchQuery: "",
      topChat: {
        name: "Mathew Anderson",
        job: "Marketing Director",
        avatar: require('@/assets/userimg.svg'),
        status: "available",
      },
      chats: [
        { id: 1, name: "Michell Flintoff", time: "25 Minutes", message: "you: Hey! How are you?", status: "available", active: true, avatar: require('@/assets/id1.svg') },
        { id: 2, name: "Bianca Anderson", time: "30 Minutes", message: "Are you free tomorrow?", status: "busy", active: false, avatar: require('@/assets/id26.svg') },
        { id: 3, name: "Andrew Johnson", time: "2 hours", message: "Let's catch up this weekend!", status: "idle", active: false, avatar: require('@/assets/id3.svg') },
        { id: 4, name: "Mark Strokes", time: "5 days", message: "I sent you the notes.", status: "available", active: false, avatar: require('@/assets/id4.svg') },
        { id: 6, name: "Bianca Anderson", time: "30 Minutes", message: "Thanks for the help yesterday!", status: "idle", active: false, avatar: require('@/assets/id26.svg') },
      ],
    };
  },
  computed: {
    filteredChats() {
      return this.chats.filter(chat =>
        chat.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    toggleSortMenu() {
      this.showSortMenu = !this.showSortMenu;
    },
    handleSort(type) {
      if (type === 'name') {
        this.chats.sort((a, b) => a.name.localeCompare(b.name));
      } else if (type === 'date') {
        this.chats.sort((a, b) => new Date(b.time) - new Date(a.time));
      } else if (type === 'unread') {
        this.chats.forEach(chat => chat.active = true);
      }
      this.showSortMenu = false;
    }
  }
};
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease-in-out;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.avatar {
  width: 2.5rem;
  height: 2.5rem;
}

.status-indicator {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 0.6rem;
  height: 0.6rem;
  border-radius: 50%;
  border: 1px solid white;
}

.available { background-color: green; }
.busy { background-color: red; }
.idle { background-color: yellow; }

.sort-menu {
  top: 100%;
  left: 0;
  z-index: 10;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  padding: 8px;
  width: fit-content;
}

.sort-menu button {
  text-align: left;
  width: 100%;
  display: block;
  padding: 6px 12px;
}

.sort-menu button:hover {
  background-color: #f6f7f9;
}

.py-1.d-flex:hover {
  background-color: #F6F7F9;
}

.toggle-chats {
  cursor: pointer;
  display: flex;
  align-items: center;
}

.toggle-chats i {
  margin-left: 5px;
  font-size: 0.8rem;
}
</style>