<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light shadow w-100 rounded">
      <div class="container-fluid d-flex justify-content-between w-100">
        <!-- Chat Brand -->
        <a class="navbar-brand fw-bold" href="#">Chat</a>
  
        <!-- Breadcrumb-like Navigation -->
        <span class="navbar-text d-flex align-items-center">
          <i class="fs-5 bi bi-house-door-fill pe-2 text-secondary"></i>
          <span class="text-muted"> / </span>
          <small class="chat-colored px-2 ms-3 fw-semibold">Chat</small>
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
    background: rgb(169, 180, 247);
    color: rgb(57, 54, 139);
    border-radius: 8px;
    padding: 5px 10px;
  }
  
  </style>
  