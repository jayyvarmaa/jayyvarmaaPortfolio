<template>
  <div style="overflow: hidden;">
    <h1 style="margin-bottom: 50px;">Hello!</h1>
    <div class="paragraph">
      <div>
        <span class="typing-text" :class="{ 'hide-cursor': !showCursor }" style="font-size: 100px; font-family: 'Karla', sans-serif; font-weight: 900; white-space: nowrap; text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3); letter-spacing: -0.02em;">{{ displayedName }}</span><br/><br/>
        <div class="body-content">
          <h4>a passionate <span class="highlight-text">game developer</span> and <span class="highlight-text">programmer</span>.<br/>
          I love building immersive experiences, from small Unity projects to larger open-world concepts, experimenting with gameplay mechanics, environments, and storytelling.</h4>
        </div>
      </div>

      <div style="margin-top: 20px;" class="body-content">
        <h4>I've worked on both game and non-game projects, and I enjoy exploring different tech stacks while continuously improving my skills.<br/>
        Currently, I'm developing my own projects under VarmaBrothers and sharing my journey as I grow as a developer.</h4>
      </div>

      <div style="margin-top: 20px;" class="body-content">
        <h4>You can reach me anytime here on <a href="https://instagram.com/jayyvarmaa" target="_blank">Instagram</a> or through my <router-link to="/contact">other platforms</router-link>.</h4>
      </div>
    </div>

  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "About",
  data() {
    return {
      displayedName: '',
      fullName: "I'm Jay Varma,",
      showCursor: false,
      isFirstLoad: false,
      preventScroll: (e: Event) => {
        e.preventDefault();
        e.stopPropagation();
        return false;
      }
    };
  },
  mounted() {
    // Check if this is a fresh page load (not tab switch or theme change)
    const isPageLoad = !sessionStorage.getItem('hasVisitedAbout');
    
    if (isPageLoad) {
      this.isFirstLoad = true;
      sessionStorage.setItem('hasVisitedAbout', 'true');
      
      // Start typing animation after a short delay
      setTimeout(() => {
        this.startTypingAnimation();
      }, 500);
      
      // Start body content animation after typing completes
      setTimeout(() => {
        this.startBodyAnimation();
      }, 3000); // 500ms delay + 2000ms typing + 500ms buffer
    } else {
      // If not first load, show name immediately and body content
      this.displayedName = this.fullName;
      this.showCursor = false; // No cursor when not animating
      this.$nextTick(() => {
        const bodyElements = document.querySelectorAll('.body-content');
        bodyElements.forEach((el) => {
          const element = el as HTMLElement;
          element.style.opacity = '1';
          element.style.transform = 'translateY(0)';
        });
      });
    }
    
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
  },
  methods: {
    startTypingAnimation() {
      this.showCursor = true; // Show cursor during animation
      let currentIndex = 0;
      const typingInterval = setInterval(() => {
        if (currentIndex <= this.fullName.length) {
          this.displayedName = this.fullName.slice(0, currentIndex);
          currentIndex++;
        } else {
          clearInterval(typingInterval);
          // Remove cursor after animation completes
          setTimeout(() => {
            this.showCursor = false;
          }, 500); // Small delay before removing cursor
        }
      }, 2000 / this.fullName.length); // 2 seconds total
    },
    startBodyAnimation() {
      const bodyElements = document.querySelectorAll('.body-content');
      bodyElements.forEach((el, index: number) => {
        setTimeout(() => {
          const element = el as HTMLElement;
          element.classList.add('animate-in');
        }, index * 200); // Stagger each element by 200ms
      });
    }
  }
});
</script>

<style scoped>
.paragraph {
  max-width: 700px;
  margin-bottom: 20px;
}

/* Typing animation cursor */
.typing-text {
  font-family: 'Karla', sans-serif;
  font-weight: 900; /* Karla Black */
  white-space: nowrap; /* Prevent text wrapping */
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
  letter-spacing: -0.02em;
  font-stretch: ultra-condensed;
}

.typing-text::after {
  content: '|';
  animation: blink 1s infinite;
  color: inherit;
  font-weight: 900; /* Ensure cursor is also bold */
  opacity: 1;
  transition: opacity 0.3s ease;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
}

.typing-text.hide-cursor::after {
  content: ''; /* Remove cursor content completely */
  animation: none; /* Stop blinking animation */
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

/* Body content animation */
.body-content {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.body-content.animate-in {
  opacity: 1;
  transform: translateY(0);
}

/* Red highlight for quoted text */
.highlight-text {
  color: #D32F2F;
  font-weight: 600;
}

@media only screen and (min-width: 620px){
  .paragraph {
    float: left;
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