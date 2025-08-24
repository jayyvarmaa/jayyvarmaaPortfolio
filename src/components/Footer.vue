<template>
  <div class="footer">
    
    <div class="left">Portfolio by <strong>Jay Varma</strong></div>
    <div class="right">Reach me at <a href="mailto:jaymayurvarma@gmail.com">jaymayurvarma@gmail.com</a> or <router-link to="/contact">through here</router-link></div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  name: "Footer"
});
</script>

<style scoped lang="less">

@import '../css/variables.less';

.footer {
  width: 100%;
  font-size: 0.8em;
  opacity: 1;
  padding: 15px 0 20px 0;
  position: fixed;
  bottom: -5px;
  left: 0;
  right: 0;
  z-index: 1000;
  background: none;
  margin: 0;
  box-sizing: border-box;
  min-height: 50px;
}

.footer a {
  color: @textColor;
  opacity: 0.8;
}

.footer a:hover {
  color: @accentColor;
  opacity: 1;
}

/* Dark mode footer styling */
[data-theme="dark"] .footer {
  color: @darkTextColor;
  background: none;
}

[data-theme="dark"] .footer a {
  color: @darkTextColor;
}

[data-theme="dark"] .footer a:hover {
  color: @accentColor;
}

.left, .right {
    padding: 0;
    margin: 0;
    text-align: center;
  }

@media only screen and (min-width: 620px){

  .footer {
    padding: 8px 0;
  }

  .left, .right {
    padding: 0 20px;
    margin: 0;
  }

  .left {
    float: left;
  }

  .right {
    float:right;
  }
}
</style>