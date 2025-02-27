<template>
  <div class="sidebar d-flex flex-column">
    <!-- Logo Section -->
    <div class="logo-section d-flex align-items-center justify-content-center">
      <img src="@/assets/logo.png" alt="Logo" class="logo">
      <p class="text-dark ms-2">HI TEAM</p>
    </div>

    <hr class="divider">

    <!-- Menu Items -->
    <nav class="nav flex-column"> 
      <a href="#" class="menu-item active">
        <i class="bi bi-house-door"></i> Dashboard
      </a>
      <a href="#" class="menu-item"><i class="bi bi-box"></i> Orders</a>
      <a href="#" class="menu-item"><i class="bi bi-people"></i> Passengers</a>
      <a href="#" class="menu-item"><i class="bi bi-truck"></i> Captains</a>
      <a href="#" class="menu-item"><i class="bi bi-grid"></i> Categories</a>
      
      <hr class="divider">
      <a href="#" class="menu-item"><i class="bi bi-file-earmark-text"></i> Settlement</a>
      <hr class="divider">
      
      <a href="#" class="menu-item"><i class="bi bi-chat-dots"></i> Contact</a>
      <a href="#" class="menu-item"><i class="bi bi-star"></i> Reviews</a>
      
      <hr class="divider">

      <!-- Permissions with Toggle -->
      <a href="#" class="menu-item" @click="togglePermissions">
        <i class="bi bi-shield-lock"></i> Permissions   
        <i class="bi" :class="permissionsOpen ? 'bi-chevron-up' : 'bi-chevron-down'" style="margin-left:auto;"></i>
      </a>

      <div v-if="permissionsOpen" class="submenu">
        <a href="#" class="menu-item"><i class="bi bi-translate"></i> Translation</a>
        <a href="#" class="menu-item"><i class="bi bi-camera-video"></i> Education Video</a>
        <a href="#" class="menu-item"><i class="bi bi-gear"></i> Settings</a>
        <a href="#" class="menu-item"><i class="bi bi-layout-text-window"></i> Content</a>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  data() {
    return {
      permissionsOpen: true
    };
  },
  methods: {
    togglePermissions() {
      this.permissionsOpen = !this.permissionsOpen;
    }
  }
};
</script>

<style scoped>

.sidebar {
  width: auto; /* Increased width */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 12px; /* Smaller padding */
  background: white;
}

.logo {
  width: 40px; /* Smaller logo size */
  height: 40px;
}

/* Divider */
.divider {
  border-color: #3b3838;
  width: 90%;
  margin: 8px auto; /* Reduced margin */
}

/* Menu Item */
.menu-item {
  display: flex;
  align-items: center;
  color: #000000;
  padding: 5px; /* Smaller padding */
  font-size: 12px; /* Smaller font size */
  margin: 4px; /* Reduced margin */
  text-decoration: none;
  border-radius: 8px; /* Smaller border radius */
  transition: background 0.3s ease, color 0.3s ease;
}

.menu-item i {
  margin-right: 10px; /* Smaller icon spacing */
  font-size: 16px; /* Smaller icon size */
  color: #8f8f8f;
}

/* Hover */
.menu-item:hover {
  background-color: #d9cfeb;
  color: #000000;
}

/* Active */
.menu-item.active {
  background-color: #8964ce;
  color: white;
}

.menu-item.active i {
  color: white;
}

.submenu {
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.submenu .menu-item {
  padding-left: 16px; /* Smaller padding for submenu items */
  font-size: 12px; /* Smaller submenu font size */
}

</style>
