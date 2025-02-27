<template>
  <body class="container-fluid">
    <div class="row d-flex g-0">
      <!-- Sidebar -->
      <div class="col-2 p-0 m-0 d-flex">
        <side-bar />
      </div>

      <!-- Main Content -->
      <div class="col-10">
        <nav-bar />

        <!-- Chat Container inside v-card -->
        <div class="d-flex justify-content-center mt-3">
          <v-card class="chat-card">
            <div class="chat-container rounded">
              <!-- ChatNav Full Width -->
              <div class="row g-0">
                <div class="col-12">
                  <chat-nav class="chat-nav" />
                </div>
              </div>

              <!-- Chat Content: RecentChat & MainChat -->
              <div class="row g-0 chat-body">
                <!-- Recent Chat (Left) -->
                <div class="col-4 d-flex flex-column p-0">
                  <recent-chat class="recent-chat" />
                </div>

                <!-- Main Chat (Right) -->
                <div class="col-8 d-flex flex-column p-0">
                  <main-chat class="chat-content" />
                </div>
              </div>
            </div>
          </v-card>
        </div>
      </div>
    </div>
  </body>
</template>

<script>
import NavBar from './components/NavBar.vue';
import SideBar from './components/SideBar.vue';
import ChatNav from './components/ChatNav.vue';
import MainChat from './components/MainChat.vue';
import RecentChat from './components/RecentChat.vue';
import '@/assets/style.css';

export default {
  components: {
    NavBar,
    SideBar,
    ChatNav,
    MainChat,
    RecentChat
  }
};
</script>
<style scoped>


.chat-card {
  width: auto;
  height: 100%;
  padding:5%;
  margin:5%; 
  box-shadow: 0px 4px 10px rgba(20, 18, 18, 0.1);
  border-radius: 12px;
  background: #e8e8e8;
  display: flex;
  flex-direction: column;
}


.chat-container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  margin: 0;
  padding: 0;

}

.chat-nav {
  text-align: center;
  margin-bottom: 2%;
}

/* Chat Body: RecentChat & MainChat */
.chat-body {
  display: flex;
  width: 100%;
  flex-grow: 1;
  height: 100%;
  margin: 0;
  padding: 0;
}

/* Recent Chat */
.recent-chat {
  padding: 0;
  height: 100%;
  display: flex;
  flex-direction: column;
  background: #f9f9f9;
  border-radius: 8px 0 0 8px; /* Round top-left and bottom-left */
}



.chat-content {
  padding: 0;
  background: #fff;
  border-radius:  0 8px 8px 0;
  height: 100%;
  display: flex;
  flex-direction: column;
}

/* Sidebar full height */
.col-2 {
  height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Ensure that navbar stays on top */
nav-bar {
  top: 0;
  z-index: 1000;
}


</style>
