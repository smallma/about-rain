<script setup>
  defineProps({
    name: String,
    hashtag: String
  })
</script>

<template>
  <a class="header_tab" v-bind:href="hashtag">{{ name }}</a>
</template>



<style lang="scss" scoped>
  .header_tab {
    display: inline-block;
    position: relative;
    padding: 10px 0;
    color: #fff;
    font-size: 1rem;
    text-align: center;
    text-decoration: none;
    min-width: 120px;

    &::after {
      display: block;
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      max-width: 0;
      height: 2px;
      background: #fff;
      transition: all 400ms;
      content: '';
    }

    &:hover {
      &::after {
        max-width: 100%;
      }
    }
  }
</style>