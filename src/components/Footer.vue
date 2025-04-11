<template>
  <div class="footer">
    <span class="copy-right">© 2025 Rain Lin. All rights reserved</span>
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
    box-sizing: border-box;

    // z-index: 1000;
    // bottom: 0;
    // left: 0;
    padding: 10px 20px;
    width: 100vw;
    text-align: center;
    background: rgb(0 0 0 / 70%);

    .copy-right {
      color: #999;
      font-weight: 600;
      font-size: 14px;
    }
  }
</style>