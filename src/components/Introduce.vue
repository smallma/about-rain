<template>
  <div class="introduce" id="about">
    <video class="introduce_video" width="100%" controls muted>
    <!-- <video class="introduce_video" width="100%" controls loop autoplay muted> -->
      <source src="../assets/coding.mp4" type="video/mp4">
    </video>
    <div class="introduce_video-mask">></div>
    <div class="introduce_content">
      <span class="content-line-1">Hi</span>
      <span class="content-line-2">I am Rain</span>
      <span class="content-line-3">I live in Taipei</span>
      <span class="content-line-4">Hi</span>
    </div>
  </div>
</template>

<script>
export default {
  setup () {
    

    return {}
  }
}
</script>

<style lang="scss" scoped>

.introduce {
  position: relative;
  width: 100%;
  height: 150vh;

  .introduce_video {
    position: sticky;
    top: 0;
    left: 0;
    margin-left: -90%;
    width: auto;
    height: 100vh;
    transform: matrix3d(0.64398, 0.089011, 0, 0.000244, 0.000904, 1.0003, 0, -0.00001, 0, 0, 1, 0, -208.935962, -15.942201, 0, 1);
    transform-origin: 1100px 99px 0;
  }

  .introduce_video-mask {
    position: absolute;
    top: 0;
    left: 29%;
    width: 100vw;
    height: 150vh;
    // background: rgba(255, 255, 255, 0.3);
    backdrop-filter: blur(2px);
  }

  .introduce_content {
    position: absolute;
    top: 0;
    left: 50%;
    margin-left: -300px;
    width: 500px;
    height: 150vh;

    .content-line-1 {
      position: sticky;
      color: #fff;
      font-size: 80px;
    } 
  }

}

</style>