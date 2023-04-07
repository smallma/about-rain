<template>
  <div class="footer">
    <span class="copy-right">© 2021 Rain Lin. All rights reserved</span>
  </div>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style lang="scss" scoped>
  .footer {
    position: relative;
    // z-index: 1000;
    // bottom: 0;
    // left: 0;
    padding: 10px 20px;
    width: 100vw;
    text-align: center;
    background: rgba(0, 0, 0, 0.7);

    .copy-right {
      color: #fff;
      font-size: 1rem;
    }
  }
</style>