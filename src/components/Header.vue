<script setup>
    import HeaderTab from './HeaderTab.vue'
</script>

<template>
  <div class="header">
    <div class="header-left"></div>
    <div class="header-right">
      <HeaderTab name="About" hashtag="#about"/>
      <HeaderTab name="Portfolio" hashtag="#portfolio"/>
      <HeaderTab name="Contact" hashtag="#contact"/>
    </div>
  </div>
</template>


<style lang="scss" scoped>
  .header {
    position: fixed;
    z-index: 1000;
    top: 0;
    width: 100%;
    background: rgb(0 0 0 / 70%);

    .header-right {
      position: relative;
      margin-right: 0;
      text-align: right;
    }
  }
</style>