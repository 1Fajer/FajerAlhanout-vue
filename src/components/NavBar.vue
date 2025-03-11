<template>
  <div class="navbar-container">
    <div class="row p-2">
      <div class="col-3 d-flex gap-4 ps-5 align-items-center">
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
        <!-- User Profile Image -->
        <img src="@/assets/userimg.svg" class="user">
      </div>
    </div>

    <!-- Language Dropdown -->
    <div v-if="showLanguages" class="language-dropdown">
      <ul>
        <li @click="changeLanguage('en')">English</li>
        <li @click="changeLanguage('ar')">Arabic</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      language: 'en', // default language is English
      showLanguages: false, // to toggle the dropdown visibility
    };
  },
  methods: {
    toggleLanguage() {
      this.showLanguages = !this.showLanguages; // Toggle language dropdown
    },
    changeLanguage(lang) {
      this.language = lang;
      this.showLanguages = false; // Close the dropdown after selection
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
}

.flag{
  width:1.4rem;
  height:1.4rem;
  border-radius: 50%;
}
.user{
  width:2.1rem;
  height:2.1rem;
  border-radius: 50%;
  
}

/* Language Dropdown Styles */
.language-dropdown {
  position: absolute;
  top: 40px;
  right: 5%;
  background-color: white;
  border-radius: 5px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  width: 100px;
}

.language-dropdown ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.language-dropdown ul li {
  padding: 10px;
  cursor: pointer;
}

.language-dropdown ul li:hover {
  background-color: #f0f0f0;
}

/* Language Selector */
.language-selector {
  cursor: pointer;
}
</style>
