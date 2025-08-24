<template>
  <transition name="fade">
    <div v-if="visible">
      <div class="overlay">
      </div>
      <div class="dialog" :style="{ 'background-color': color }">
        <h1 class="dialog-title">{{ title }}</h1>
        <div @click="$emit('close')" class="dialog-close"><i class="fa fa-times fa-lg fa-fw"></i></div>
        <div class="dialog-content">
          <div v-html="htmlContent"></div>
          <div class="dialog-bottom">
          <a @click="$emit('close')" class="dialog-close-button">Close</a>
        </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "ProjectDetailsOverlay",
  props: {
    visible: Boolean,
    color: String,
    title: String,
    htmlContent: String,
  },
  data() {
    return {
      isDarkMode: false
    };
  },
  mounted() {
    // Check current theme
    const savedTheme = localStorage.getItem('theme');
    this.isDarkMode = savedTheme === 'light' ? false : true; // Default to dark mode
    
    // Listen for theme changes
    this.$root.$on('themeChanged', (isDark: boolean) => {
      this.isDarkMode = isDark;
    });
  },
  beforeDestroy() {
    this.$root.$off('themeChanged');
  },
  methods: {
    getImage: function(url: string) {
      console.log("fetching image " + url);
    }
  }
});
</script>

<style scoped>
.overlay {
  background-color: rgba(0,0,0,0.7);
  z-index: 10000;
  position:fixed;
  top:0px;
  left:0px;
  right:0px;
  bottom: 0px;
}

.dialog {
  position:absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  z-index: 10001;
  margin: 20px;
  padding-bottom: 10px;
  color:white;
}

iframe {
  width: 100%;
}

h1.dialog-title {
    text-align: center;
    font-size: 1.3em;
    margin: 0px;
    padding: 22px;
}

.dialog-content {
  padding: 20px;
  background-color: #ffffff;
  color: #2d2d2d;
  transition: all 0.3s ease;
}

/* Dark mode styling for dialog content */
[data-theme="dark"] .dialog-content {
  background-color: #1e1e1e;
  color: #e0e0e0;
}

[data-theme="dark"] .dialog-content .paragraph {
  color: #e0e0e0;
}

[data-theme="dark"] .dialog-content ul li {
  color: #e0e0e0;
}

[data-theme="dark"] .dialog-content .notice {
  background-color: rgba(211, 47, 47, 0.2);
  border-left: 4px solid #D32F2F;
  color: #e0e0e0;
}

.dialog-close {
  position: absolute;
  top: 20px;
  right: 20px;
  cursor:pointer;
  font-size: 1.2em;
  font-weight: 100;
  transition: all 0.2s ease;
}
.dialog-close:hover {
  opacity: 0.8;
  transform: scale(1.1);
}

.dialog-bottom {
  text-align: center;
}

a.dialog-close-button {
  cursor:pointer;
  font-size: 1.4em;
  display: inline-block;
  margin: 0 auto;
  color: #D32F2F;
  padding: 10px 20px;
  border: 2px solid #D32F2F;
  border-radius: 4px;
  transition: all 0.2s ease;
}

a.dialog-close-button:hover {
  background-color: #D32F2F;
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 4px 8px rgba(211, 47, 47, 0.3);
}

@media only screen and (min-width: 620px){
  .dialog {
    margin: 0 auto;
    margin-top: 80px;
    margin-bottom: 40px;
    max-width: 1000px;
  }

  h1.dialog-title {
    font-size: 1.6em;
  }

  .dialog-content {
    padding: 40px;
  }
}
</style>
