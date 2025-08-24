<template>
  <div style="overflow: hidden;">
    
    <h1>Let's get in touch</h1>

    <div style="margin-bottom:40px;">
      I'm open to collaborations in game development and interactive media!<br/>
      Feel free to contact me about any opportunity, discuss projects, or just chat about game development, technology, or creative ideas.
    </div>

    <ul>
      <li>
        <i class="fa fa-envelope-o fa-lg fa-fw"></i>
        <a href="mailto:jaymayurvarma@gmail.com" target="_blank">jaymayurvarma@gmail.com</a>
      </li>
      <li>
        <i class="fa fa-linkedin fa-lg fa-fw" style="vertical-align: -5%;"></i>
        <a href="https://www.linkedin.com/in/jayyvarmaa" target="_blank">LinkedIn</a>
      </li>
      <li>
        <i class="fa fa-instagram fa-lg fa-fw"></i>
        <a href="https://instagram.com/jayyvarmaa" target="_blank">Instagram</a>
      </li>
      <li>
        <i class="fa fa-reddit fa-lg fa-fw"></i>
        <a href="https://reddit.com/user/jayyvarmaa" target="_blank">Reddit</a>
      </li>
      <li>
        <i class="fa fa-github fa-lg fa-fw"></i>
        <a href="https://github.com/jayyvarmaa" target="_blank">GitHub</a>
      </li>
      <li>
        <i class="fa fa-coffee fa-lg fa-fw"></i>
        <a href="https://buymeacoffee.com/jayyvarmaa" target="_blank">Buy Me A Coffee ☕</a>
      </li>
    </ul>


  </div>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  name: "Contact",
  data() {
    return {
      preventScroll: (e: Event) => {
        e.preventDefault();
        e.stopPropagation();
        return false;
      }
    };
  },
  mounted() {
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
  }
});
</script>

<style scoped>
ul {
  list-style: none;
  padding-inline-start: 0px;
}

li {
    line-height: 1.8em;
    font-size: 1.2em;
  }

@media only screen and (min-width: 620px){
  ul {
    padding-inline-start: 40px;
  }

  li {
    line-height: 2em;
    font-size: 1.4em;
  }
}

i {
  margin-right: 20px;
}
</style>
