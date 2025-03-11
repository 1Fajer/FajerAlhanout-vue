<template>
  <div class="d-flex flex-column min-vh-100 p-3 bg-white" style="font-size: 0.85rem;">
    <!-- Logo Section -->
    <div class="d-flex align-items-center justify-content-start">
      <img src="@/assets/logo.png" alt="Logo" class="rounded-circle" width="60rem" height="60rem">
      <p class="ms-2 mb-0">HI TEAM</p>
    </div>
    <!-- Menu Items -->
    <nav class="nav flex-column gap-1">
      <a href="#" class="nav-link active  text-light rounded shadow " style="background-color: #635BFF;">
        <i class="bi bi-house-door me-1"></i> Dashboard
      </a>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-box me-1" style="color: #98A4AE;"></i> Orders</a>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-people me-1" style="color: #98A4AE;"></i> Passengers</a>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-truck me-1" style="color: #98A4AE;"></i> Captains</a>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-grid me-1" style="color: #98A4AE;"></i> Categories</a>
      
      <hr>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-file-earmark-text me-1" style="color: #98A4AE;"></i> Settlement</a>
      <hr>
      
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-chat-dots me-1" style="color: #98A4AE;"></i> Contact</a>
      <a href="#" class="nav-link text-dark rounded"><i class="bi bi-star me-1" style="color: #98A4AE;"></i> Reviews</a>
      
      <hr>

      <!-- Permissions with Toggle -->
      <a href="#" class="nav-link text-dark d-flex align-items-center justify-content-between rounded" @click="togglePermissions">
        <span><i class="bi bi-shield-lock me-1" style="color: #98A4AE;"></i> Permissions</span>  
        <i class="bi" :class="permissionsOpen ? 'bi-chevron-up' : 'bi-chevron-down'" style="color: #98A4AE;"></i>
      </a>

      <div v-if="permissionsOpen" class="ms-0">
        <a href="#" class="nav-link text-dark rounded ps-3"><i class="bi bi-translate me-1" style="color: #98A4AE;"></i> Translation</a>
        <a href="#" class="nav-link text-dark rounded ps-3"><i class="bi bi-camera-video me-1" style="color: #98A4AE;"></i> Education Video</a>
        <a href="#" class="nav-link text-dark rounded ps-3"><i class="bi bi-gear me-1" style="color: #98A4AE;"></i> Settings</a>
        <a href="#" class="nav-link text-dark rounded ps-3"><i class="bi bi-layout-text-window me-1" style="color: #98A4AE;"></i> Content</a>
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
a:hover {
  background: #635BFF;
  color: white !important;
  box-shadow: var(--bs-shadow);
}


a:hover i {
  color: white !important;
}
</style>
