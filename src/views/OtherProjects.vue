<template>
  <div style="overflow: hidden;">
    <h1>Brands & Creative Projects</h1>

    <div style="margin-bottom: 15px;">
      I've built several brands and creative ventures including RansomType, BeyondWideAngle, and VarmaBrothers.<br/>
      Each represents a different aspect of my creative and entrepreneurial journey in digital innovation.
    </div>

    <!-- Brand Logos Section -->
    <div class="brands-container">
      <div class="brand-logo" @click="openRansomType">
        <img :src="ransomTypeLogo" alt="RansomType Logo" />
      </div>
      
      <div class="brand-logo" @click="openBeyondWideAngle">
        <img :src="beyondWideAngleLogo" alt="BeyondWideAngle Logo" />
      </div>
      
      <div class="brand-logo" @click="openVarmaBrothers">
        <img src="img/vblogo.png" alt="VarmaBrothers Logo" />
      </div>
    </div>

    <ProjectDetailsOverlay
      v-on:close="showPopup = false"
      :visible="showPopup"
      :title="popupTitle"
      :htmlContent="popupContent"
      :color="popupColor"
    />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import ProjectDetailsOverlay from "@/components/ProjectDetailsOverlay.vue";
import otherProjectsData from "@/data/OtherProjectsData";
import ProjectData from "@/data/ProjectData";

export default Vue.extend({
  name: "OtherProjects",
  components: {
    ProjectDetailsOverlay,
  },
  data() {
    return {
      projects: otherProjectsData,
      showPopup: false,
      popupTitle: "",
      popupColor: "",
      popupContent: "",
      isDarkMode: false,
      preventScroll: (e: Event) => {
        e.preventDefault();
        e.stopPropagation();
        return false;
      }
    };
  },
  computed: {
    ransomTypeLogo(): string {
      return this.isDarkMode ? 'img/RansomTypeLogoDarkMode.png' : 'img/RansomTypeLogoLightMode.png';
    },
    beyondWideAngleLogo(): string {
      return this.isDarkMode ? 'img/BWADarkMode.png' : 'img/BWALightMode.png';
    }
  },
  mounted() {
    // Check current theme using same method as Header component
    const savedTheme = localStorage.getItem('theme');
    this.isDarkMode = savedTheme === 'light' ? false : true; // Default to dark mode
    
    // Also check data-theme attribute as fallback
    if (!savedTheme) {
      this.isDarkMode = document.documentElement.getAttribute('data-theme') === 'dark' || true; // Default to dark
    }
    
    // Listen for theme changes
    this.$root.$on('themeChanged', (isDark: boolean) => {
      this.isDarkMode = isDark;
    });
    
    // Disable scrolling on the entire page
    document.body.style.overflow = 'hidden';
    document.documentElement.style.overflow = 'hidden';
    document.body.style.position = 'fixed';
    document.body.style.width = '100%';
    document.body.style.height = '100%';
    
    // Add event listeners to prevent all scroll events
    window.addEventListener('wheel', this.preventScroll, { passive: false });
    window.addEventListener('touchmove', this.preventScroll, { passive: false });
    window.addEventListener('scroll', this.preventScroll, { passive: false });
    document.addEventListener('wheel', this.preventScroll, { passive: false });
    document.addEventListener('touchmove', this.preventScroll, { passive: false });
    document.addEventListener('scroll', this.preventScroll, { passive: false });
  },
  beforeDestroy() {
    // Re-enable scrolling when leaving the page
    document.body.style.overflow = '';
    document.documentElement.style.overflow = '';
    document.body.style.position = '';
    document.body.style.width = '';
    document.body.style.height = '';
    
    // Remove event listeners
    window.removeEventListener('wheel', this.preventScroll);
    window.removeEventListener('touchmove', this.preventScroll);
    window.removeEventListener('scroll', this.preventScroll);
    document.removeEventListener('wheel', this.preventScroll);
    document.removeEventListener('touchmove', this.preventScroll);
    document.removeEventListener('scroll', this.preventScroll);
    
    // Clean up event listener
    this.$root.$off('themeChanged');
  },
  methods: {
    openRansomType() {
      window.open('https://ransomtype.vercel.app/', '_blank');
    },
    openBeyondWideAngle() {
      window.open('https://youtube.com/@BeyondWideAngle', '_blank');
    },
    openVarmaBrothers() {
      window.open('https://varmabrothers.gumroad.com/', '_blank');
    },
    showDetails: function (item: ProjectData) {
      this.popupTitle = item.name;
      this.popupColor = item.accentColor;
      this.popupContent = item.htmlDescription;
      this.showPopup = true;
      window.scrollTo(0,0);
    },
  },
});
</script>

<style scoped>
.brands-container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 5px;
  margin-top: 5px;
}

.brand-logo {
  cursor: pointer;
  transition: all 0.3s ease;
  margin: 0;
  padding: 2px 0;
}

.brand-logo:hover {
  transform: translateY(-8px) scale(1.05);
  filter: brightness(110%);
}

.brand-logo img {
  max-width: 100%;
  height: auto;
  display: block;
  transition: all 0.3s ease;
  max-height: 90px;
  width: auto;
}

.brand-logo:hover img {
  transform: scale(1.02);
}

@media only screen and (min-width: 620px) {
  .brand-logo img {
    max-height: 110px;
  }
}

@media only screen and (min-width: 1000px) {
  .brand-logo img {
    max-height: 130px;
  }
}

/* Additional scroll prevention */
* {
  overscroll-behavior: none;
}

body {
  touch-action: none;
  -ms-touch-action: none;
}

html, body {
  overflow: hidden !important;
  position: fixed !important;
  width: 100% !important;
  height: 100% !important;
}
</style>
