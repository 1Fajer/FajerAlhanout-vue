<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light shadow-sm rounded">
      <div class="container-fluid d-flex justify-content-between">
        <!-- Chat Brand -->
        <a class="navbar-brand fw-semibold ps-2 " href="#">Chat</a>
  
        <!-- Breadcrumb-like Navigation -->
        <span class="navbar-text d-flex align-items-center">
          <i class="bi bi-house"></i>
          <span class="fw-bold mx-2"> / </span>
          <small class="chat-colored p-1 rounded">Chat</small>
        </span>
      </div>
    </nav>
  </template>
  
  <style scoped>
  .navbar {
    width: 100%;
    flex: 1;
    display: block; 

    
  }
  
  /* Chat Highlight */
  .chat-colored {
    background: rgb(211, 217, 255);
    color: rgb(93, 90, 183);
  }
  
  </style>
  