<script setup>
    import ReplaceWording from './ReplaceWording.vue'
</script>


<template>
  <div class="introduce" id="about">
    <!-- <video class="introduce_video" width="100%" controls muted> -->
    <video class="introduce_video" width="100%" controls loop autoplay muted>
      <source :src="'./images/coding.mp4'" type="video/mp4">
    </video>
    <div class="introduce_video-mask"></div>
    <div class="introduce_content">
      <div class="content-sticky">

      <span class="content-line content-line-1">Hello</span>
      <span class="content-line content-line-2">I am <span class="special">Rain</span></span>
      <span class="content-line content-line-3">I live in Taipei</span>
      <span class="content-line content-line-4">I love <ReplaceWording :wodingList="['Photography', 'Lego', 'Coding']" /></span>

      
      </div>
    </div>

    <div class="introduce_belt">
      <div class="belt-sticky">
        <span class="belt"><ReplaceWording :wodingList="['Javascript', 'PUG', 'SCSS', 'Python']" /> Developer</span>
      </div>
    </div>
  </div>
</template>


<style lang="scss" scoped>
.introduce {
  position: relative;
  z-index: 2;
  width: 100%;
  height: 150vh;
  background-color: #000;

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
    margin-left: 0;
    width: 500px;
    height: 150vh;

    .content-sticky {
      position: sticky;
      top: 20vh;
      height: 100vh;
    }

    .content-line {
      display: block;
      position: relative;
      color: #fff;
      font-size: 2rem;
      text-align: left;
    } 

    .content-line-1 {
      font-size: 13rem;
      transform: rotate(-13deg) translate3d(-350px, -42px, 0);
      letter-spacing: 22px;
    }

    .content-line-2 {
      .special {
        font-size: 5rem;
      }
    }

    .content-line-4 {
      .replace_wording {
        top: 21px;
        padding-left: 10px;
      }
    }
  }

  .introduce_belt {
    position: absolute;
    top: calc(150vh - 160px); 
    left: 0;
    margin-left: 0;
    width: 100vw;
    height: 160px;

    .belt-sticky {
      position: sticky;
      top: 0;
      height: 160px;

      .belt {
        display: block;
        position: relative;
        padding: 25px 20px;
        box-sizing: border-box;
        width: 100vw;
        color: #fff;
        font-size: 5rem;
        min-height: 160px;
        background: rgb(83 77 118 / 20%);

        :deep .replace_wording {
          top: 8px;
          text-align: right;

          .wording {
            width: 100%;
            color: #adffb0;
            text-align: right;
          }
        }
      }
    }
  }
}

@media all and (max-width: 731px) {
  .introduce {
    .introduce_content {
      left: 5.4%;
      margin-left: 0;
      width: 100%;

      .content-line-1 {
        left: 50%;
        margin-left: -4px;
        width: 320px;
        font-size: 80px;
        transform: rotate(15deg) translate3d(-50%, -12px, 0);
      }
    }

    .introduce_belt {
      top: calc(150vh - 100px);

      .belt-sticky {
        .belt {
          font-size: 40px;
          background: rgba(0,0,0, 0.9);
          :deep .replace_wording {
            text-align: center;

            .wording {
              text-align: center;
            }
          }
        }
      }
    }
  }
}
</style>