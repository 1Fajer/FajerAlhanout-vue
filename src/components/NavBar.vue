<template>
  <div class="navbar-container">
    <div class="row p-2">
      <div class="col-3 d-flex gap-4 align-items-center">
        <i class="bi bi-search"></i>
        <i class="bi bi-list"></i>
      </div>
      <div class="col-6"></div>
      <div class="col-3 d-flex justify-content-end gap-4 pe-5 align-items-center">
        <i class="bi bi-moon"></i>
        <i class="bi bi-bell"></i>

        <!-- Language Selector -->
        <div @click="toggleLanguage" class="language-selector">
          <img v-if="language === 'en'" src="@/assets/England.png" class="mt-1 flag">
          <img v-if="language === 'ar'" src="@/assets/Arabic.png" class="mt-1 flag">
        </div>

        <!-- User Profile Image with Dropdown -->
        <div class="user-container" @click="toggleUserMenu">
          <img src="@/assets/userimg.svg" class="user">
          <span class="dropdown-arrow">▼</span>
        </div>
      </div>
    </div>

    <!-- Language Dropdown -->
    <div v-if="showLanguages" class="language-dropdown">
      <ul>
        <li @click="changeLanguage('en')">English</li>
        <li @click="changeLanguage('ar')">Arabic</li>
      </ul>
    </div>

    <!-- User Dropdown -->
    <div v-if="showUserMenu" class="user-dropdown">
      <ul>
        <li @click="closeUserMenu">Edit Account</li>
        <li @click="closeUserMenu">Switch Account</li>
        <li @click="closeUserMenu">Sign Out</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      language: 'en', // Default language
      showLanguages: false, // Toggle language dropdown
      showUserMenu: false // Toggle user dropdown
    };
  },
  methods: {
    toggleLanguage() {
      this.showLanguages = !this.showLanguages;
    },
    changeLanguage(lang) {
      this.language = lang;
      this.showLanguages = false;
    },
    toggleUserMenu() {
      this.showUserMenu = !this.showUserMenu;
    },
    closeUserMenu() {
      this.showUserMenu = false; // Close dropdown
    }
  }
};
</script>

<style scoped>
.navbar-container {
  position: absolute;
  width: calc(100% - 16.666%);
  top: 0;
  background: white;
}

i {
  cursor: pointer;
  transition: color 0.2s ease-in-out;
  font-size: 1rem;
}

i:hover {
  color: #8964ce;
  font-size: larger;
  text-shadow: 5px 5px 10px rgba(67, 36, 123, 0.5);
}

.flag {
  width: 1.4rem;
  height: 1.4rem;
  border-radius: 50%;
}

.user {
  width: 2.1rem;
  height: 2.1rem;
  border-radius: 50%;
  cursor: pointer;
}

/* Dropdown Arrow */
.dropdown-arrow {
  font-size: 0.8rem;
  margin-left: 5px;
  cursor: pointer;
  transition: transform 0.3s ease;
}

/* User Container */
.user-container {
  display: flex;
  align-items: center;
  cursor: pointer;
}

/* Language & User Dropdowns */
.language-dropdown, .user-dropdown {
  position: absolute;
  top: 50px;
  right: 5%;
  background-color: white;
  border-radius: 8px;
  box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.15);
  width: 150px;
  z-index: 100;
  transition: all 0.3s ease-in-out;
}

/* Dropdown List */
.language-dropdown ul, .user-dropdown ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

/* Dropdown Items */
.language-dropdown ul li, .user-dropdown ul li {
  padding: 10px;
  cursor: pointer;
  transition: background 0.3s ease, box-shadow 0.3s ease;
}

/* Hover Effect */
.language-dropdown ul li:hover, .user-dropdown ul li:hover {
  background-color: #f0f0f0;
  box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.1);
}
</style>
