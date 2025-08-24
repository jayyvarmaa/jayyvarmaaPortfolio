<template>
  <div id="app">
    
    <link rel="stylesheet" href="@/assets/projects/projects.css" type="text/css">

    <Header />
    <div class="main">
      <transition name="fade" mode="out-in">
        <router-view/>
      </transition>
    </div>
    <Footer />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Helpers from './helpers';

export default Vue.extend({
  name: 'App',
  components: {
    Header, Footer
  }
});

// Preload heavy images or gifs that are used in other pages
Helpers.preloadImages([
  "img/projects/project-1-icon.png",
  "img/projects/project-2-icon.png",
  "img/projects/project-3-icon.png"
]);

</script>

<style lang="less">

@import './css/projects.less';
@import './css/variables.less';

html, body {
  margin: 0px;
  background-color: @contentBgColor !important;
  /* Hide scrollbar for Chrome, Safari and Opera */
  ::-webkit-scrollbar {
    display: none;
  }
  /* Hide scrollbar for IE, Edge and Firefox */
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

#app {
  background-color: @contentBgColor;
  color: @textColor;

  font-family: 'Karla', Helvetica, 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  font-size: 1.1em;
  line-height: 1.6em;
  text-align: justify;
}

/* Dark mode styles */
[data-theme="dark"] {
  #app {
    background-color: @darkContentBgColor;
    color: @darkTextColor;
  }
  
  html, body {
    background-color: @darkContentBgColor !important;
  }
}

/* Alternative dark mode selector for body class */
body.dark-theme {
  background-color: @darkContentBgColor !important;
  
  #app {
    background-color: @darkContentBgColor;
    color: @darkTextColor;
  }
}

h1, h2, h3, h4, h5 {
  text-align: left;
}

a {
  color: @textColor;
  text-decoration: none;
  opacity: 0.6;
  transition: all 0.2s ease;
}
a:hover, .router-link-exact-active {
  opacity: 1;
  color: @accentColor;
}

/* Dark mode link styling */
[data-theme="dark"] a {
  color: @darkTextColor;
}

[data-theme="dark"] a:hover, [data-theme="dark"] .router-link-exact-active {
  color: @accentColor;
}

h1 {
  font-size: 2.5em;
  font-weight: 100;
  margin-top: -10px;
  margin-bottom: 40px;
  margin-left: -2px; // hack to make it "seem" more aligned with smaller text content
  line-height: 1.1em;
}

.main {
    padding: 12px;
    padding-top: 160px; /* Reduced space for fixed header */
    padding-bottom: 80px; /* Increased padding for footer coverage */
    min-height: calc(100vh - 120px); /* Ensure content fills viewport */
  }

@media only screen and (min-width: 620px){

  #app {
    text-align: left;
    line-height: 1.8em;
  }

  h1 {
    margin-top: 0.67em;
    margin-bottom: 80px;
    line-height: 0.7em;
  }

  .main {
    padding: 0px 40px 100px 180px; /* Increased bottom padding for footer coverage */
    padding-top: 180px; /* Reduced space for fixed header */
    min-height: calc(100vh - 200px); /* Ensure content fills viewport */
  }

  .main, .header {
    max-width: 1200px;
    margin: 0 auto;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition-duration: 0.2s;
  transition-property: opacity;
  transition-timing-function: ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0
}

</style>
