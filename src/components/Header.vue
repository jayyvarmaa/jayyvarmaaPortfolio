<template>
  <div class="header">
    <div class="header-content">
      <div class="logo">
        <router-link to="/">
          <img :src="logoSrc" alt="Portfolio Logo" />
        </router-link>
      </div>
      <div class="nav-bar">
        <router-link to="/">About</router-link>
        <router-link to="/game-projects">Games</router-link>
        <router-link to="/other-projects">Brands</router-link>
        <router-link to="/resume">Resume</router-link>
        <router-link to="/contact">Contact</router-link>
        <button @click="toggleTheme" class="theme-toggle" :title="isDarkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode'">
          <span :class="{ 'sun-icon': isDarkMode, 'moon-icon': !isDarkMode }">{{ isDarkMode ? '☀️' : '🌙' }}</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Header",
  data() {
    return {
      isDarkMode: false
    };
  },
  computed: {
    logoSrc() {
      return this.isDarkMode ? 'img/SignatureDarkMode.png' : 'img/SignatureLightMode.png';
    }
  },
  mounted() {
    // Check for saved theme preference or default to dark mode
    const savedTheme = localStorage.getItem('theme');
    this.isDarkMode = savedTheme === 'light' ? false : true; // Default to dark mode
    this.applyTheme();
    // Emit initial theme state to other components
    this.$root.$emit('themeChanged', this.isDarkMode);
  },
  methods: {
    toggleTheme() {
      this.isDarkMode = !this.isDarkMode;
      localStorage.setItem('theme', this.isDarkMode ? 'dark' : 'light');
      this.applyTheme();
      // Emit event to notify other components
      this.$root.$emit('themeChanged', this.isDarkMode);
    },
    applyTheme() {
      document.documentElement.setAttribute('data-theme', this.isDarkMode ? 'dark' : 'light');
      // Force body class update to ensure styles are applied
      document.body.className = this.isDarkMode ? 'dark-theme' : 'light-theme';
    }
  }
});
</script>

<style scoped lang="less">

@import '../css/variables.less';

.header {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: linear-gradient(to bottom, @contentBgColor 0%, @contentBgColor 70%, fade(@contentBgColor, 0%) 100%);
  padding: 18px 0 24px 0;
}

/* Dark mode header gradient */
[data-theme="dark"] .header {
  background: linear-gradient(to bottom, @darkContentBgColor 0%, @darkContentBgColor 70%, fade(@darkContentBgColor, 0%) 100%);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.logo {
  flex-shrink: 0;
  margin-left: 100px;
  padding-top: 10px;
}

.logo img {
  height: 100px;
  width: auto;
  transition: all 0.3s ease;
}

.logo:hover img {
  transform: scale(1.05);
  filter: brightness(110%);
}

.logo a {
  border: none !important;
  opacity: 1 !important;
  color: inherit !important;
}

.logo a:hover {
  border: none !important;
  opacity: 1 !important;
  color: inherit !important;
}

.logo a.router-link-exact-active {
  border: none !important;
  opacity: 1 !important;
  color: inherit !important;
}

.nav-bar {
  text-align: right;
  line-height: 1.2em;
  display: flex;
  align-items: center;
  gap: 15px;
}

.theme-toggle {
  background: none;
  border: none;
  font-size: 1.2em;
  cursor: pointer;
  padding: 8px;
  border-radius: 50%;
  transition: all 0.2s ease;
  margin-left: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40px;
  width: 40px;
  position: relative;
  top: -2px;
}

.moon-icon {
  filter: grayscale(100%) brightness(0%); /* Makes moon black */
  display: flex;
  align-items: center;
  line-height: 1;
}

.sun-icon {
  filter: grayscale(100%) brightness(200%); /* Makes sun white */
  display: flex;
  align-items: center;
  line-height: 1;
}

.theme-toggle:hover {
  background-color: fade(@accentColor, 10%);
  transform: scale(1.1);
}

/* Dark mode theme toggle */
[data-theme="dark"] .theme-toggle {
  color: @darkTextColor;
}

[data-theme="dark"] .theme-toggle:hover {
  background-color: fade(@accentColor, 15%);
}

a {
  text-transform: uppercase;
  margin-left: 15px;
  margin-right: 15px;
  padding-bottom: 4px;
  white-space: nowrap;
  display: inline-block;
  transition: all 0.2s ease;
}

.router-link-exact-active {
  border: 0px solid @accentColor;
  border-bottom-width: 2px;
  color: @accentColor;
  opacity: 1;
}

@media only screen and (max-width: 620px){
  .header-content {
    flex-direction: column;
    align-items: center;
    gap: 15px;
    padding: 15px;
  }
  
  .logo {
    margin-left: 50px;
    padding-top: 5px;
  }
  
  .logo img {
    height: 85px;
  }
  
  .nav-bar {
    line-height: 1.1em;
    text-align: center;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
  }

  a {
    margin-left: 4px;
    margin-right: 4px;
    padding-bottom: 2px;
  }
}

</style>
