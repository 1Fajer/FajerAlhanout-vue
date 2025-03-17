<template>
  <body class="container-fluid">
    <div class="row d-flex">
      <div class="col-2 p-0 m-0 d-flex">
        <side-bar />
      </div>
      <div class="col-10">
        <nav-bar />
        <div class="d-flex mt-3">
          <v-card class="chat-card">
            <div class="chat-container rounded">
              <div class="row g-0">
                <div class="col-12">
                  <chat-nav class="chat-nav" />
                </div>
              </div>
              <div class="row g-0 chat-body  rounded shadow-sm">
                <div class="col-4 d-flex flex-column">
                  <recent-chat class="recent-chat" />
                </div>
                <div class="col-8 d-flex flex-column">
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

