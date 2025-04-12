<template>
  <div :class="'history_card ' + getAlign(history.id) + ' ' + isShow">
    <!-- <img class="history-img" v-bind:src="'@/assets/images/' + history.type + '/' + history.from + '/history_img.webp'" /> -->
    <!-- <img class="history-img" :src="require(`../../assets/images/${history.type}/${history.from}/history_img.webp`)" /> -->
    <img class="history-img" v-bind:src="'./images/' + history.type + '/' + history.from + '/history_img.webp'" />
    <span class="history-year">{{ history.year }}</span>
    <div class="info-container">
      <span class="history-info">{{ history.info }}</span>
      <div class="product-links" v-if="history.links && history.links.length">
        <a v-for="link in history.links" :key="link.name" :href="link.url" target="_blank" rel="noreferrer noopener">{{ link.name }}</a>
      </div>
    </div>
    <h2 class="history-title">{{ history.title }}</h2>

  </div>
</template>

<script>
  let timeoutIdResize;
  let timeoutIdUpdateBg;

  export default {
    name: 'HistoryCard',
    props: {
      history: {
        type: Object,
        required: true
      }
    },
    data: function(){
      return {
        offsetTop: 0,
        isShow: '',
        windowHeight: window.innerHeight,
        bgClass: 'width-first'
      };
    },
    created () {
      window.addEventListener('scroll', this.debounce(this.handleScroll));

      this.bgClass = this.history.bgHeightFull ? 'height-first' : 'width-first';

      window.addEventListener("resize", this.handleResize);
    },
    destroyed () {
      window.removeEventListener('scroll', this.debounce(this.handleScroll));
      window.removeEventListener("resize", this.handleResize);
    },
    mounted () {
      // const getOffset = (element, horizontal = false) => {
      //   if(!element) { return 0; }
      //   return getOffset(element.offsetParent, horizontal) + (horizontal ? element.offsetLeft : element.offsetTop);
      // }
      setTimeout(() => {
        this.offsetTop = this.getOffset(this.$el);
        console.log('=== mounted offsetTop update ===');
      }, 1000);
    },
    methods: {
      debounce: function (func, delay = 100) {
        let timer = null;
      
        return function(...args) {
          let context = this;
      
          clearTimeout(timer);
          timer = setTimeout(() => {
            func.apply(context, args);
          }, delay);
        }
      },
      getOffset: function (element, horizontal = false) {
        if(!element) { return 0; }
        return this.getOffset(element.offsetParent, horizontal) + (horizontal ? element.offsetLeft : element.offsetTop);
      },
      handleResize: function () {
        clearTimeout(timeoutIdResize);
        
        timeoutIdResize = setTimeout(() => {
          this.offsetTop = this.getOffset(this.$el);
          console.log('=== handleResize offsetTop update ===');
        }, 300);
      },
      getAlign: function(id) {
        const align = id % 2 == 0 ? 'left' : 'right';
        return 'text-' + align;
      },
      handleScroll (event) {
        function _updateBg () {
          const currentTime = new Date().getTime();
          // console.log('currentTime: ', currentTime);



          // const windowBottom = window.scrollY + this.windowHeight;
          // const rangeTop = this.windowHeight * 0.8;
          // const rangeBottom = this.windowHeight * 0.4;
          // if (windowBottom > this.offsetTop + rangeBottom && windowBottom < this.offsetTop + rangeTop) {
          
          //   console.log(window.scrollY, this.offsetTop, this.windowHeight, this.offsetTop + rangeTop, this.offsetTop + rangeBottom);

          //   const backgroundSrc = './images/' + this.history.type + '/' + this.history.from + '/history_bg.webp';
          //   this.isShow = ' is-show';

          //   if (window.backgroundSrc === backgroundSrc) {return; }
          //   window.backgroundSrc = backgroundSrc;
          //   console.log('backgroundSrc: ', backgroundSrc, this.bgClass);
          //   this.$emit('changeBackground', backgroundSrc, this.bgClass);
          // } else {
          //   this.isShow = '';
          // }

          const windowBottom = window.scrollY + this.windowHeight;
          const windowTop = window.scrollY;
          const rangeTop = this.windowHeight * 0.8 + windowTop;
          const rangeBottom = this.windowHeight * 0.4 + windowTop;

          const middleOfWindow = window.scrollY + this.windowHeight / 2;


          if (Math.abs(middleOfWindow - this.offsetTop) <= 300 && this.offsetTop < windowBottom && this.offsetTop > windowTop) {
            console.log(window.scrollY, this.offsetTop, this.windowHeight, middleOfWindow);

            const backgroundSrc = './images/' + this.history.type + '/' + this.history.from + '/history_bg.webp';
            this.isShow = ' is-show';

            if (window.backgroundSrc === backgroundSrc) return;

            window.backgroundSrc = backgroundSrc;
            console.log('backgroundSrc: ', backgroundSrc, this.bgClass);
            this.$emit('changeBackground', backgroundSrc, this.bgClass);

            console.log('windowBottom: ', windowBottom, ', windowTop: ', windowTop, ', middleOfWindow: ', middleOfWindow, ', this.offsetTop: ', this.offsetTop, ', this.$el.offsetHeight: ', this.$el.offsetHeight);


          } else if (this.offsetTop > rangeBottom || (this.offsetTop + this.$el.offsetHeight) < rangeTop) {
            this.isShow = '';
          }
        }
        
        // this.debounce(this._updateBg.bind(this), 300);
        _updateBg.call(this);

        // clearTimeout(timeoutIdUpdateBg);
        // timeoutIdUpdateBg = setTimeout(() => {
        //   _updateBg.call(this);
        // }, 300);
        
      }
    }
  }
</script>


<style lang="scss" scoped>
  .history_card {
    position: relative;
    left: 50%;
    padding-bottom: 100px;
    width: 440px;

    &.text-right {
      margin-left: 50px;
      text-align: left;

      .history-title {
        margin-left: -890px;
        text-align: right;

        &::before {
          right: -22px;

        }
      }

      .history-year{
        text-align: left;
      }
    }

    &.text-left {
      margin-left: -490px;
      text-align: right;

      .history-title {
        margin-left: 292px;
        text-align: left;

        &::before {
          left: -24px;
        }
      }

      .history-info {
        text-align: left;
      }
    }

    .history-year,
    .history-info {
      display: block;
      position: relative;
      color: #fff;
    }

    .info-container {
      display: block;
      position: relative;
      margin-top: 8px;
      padding: 24px;
      border-radius: 5px;
      background: rgb(0 0 0 / 70%);
      backdrop-filter: blur(10px);

      overflow: clip;
      border-radius: 8px;

      .history-info,
      .product-links {
        flex: 100%;
      }
    }

    .history-year {
      margin-top: -24px;
      margin-left: 11px;
      color: #fff;
      font-size: 50px;
      font-weight: bold;
      text-shadow: 4px 2px 5px #181818;
    }

    .history-title {
      display: block;
      position: absolute;

      // top: 50%;
      top: 90px;
      left: 50%;
      width: 600px;
      color: #fff;
      font-weight: 600;
      font-size: 1rem;

      &::before {
        display: block;
        position: absolute;
        top: 50%;
        width: 4px;
        height: 15px;
        background: rgb(255 255 255 / 50%);
        transform: translateY(-50%);
        content: '';
      }
    }

    .history-info {
      line-height: 1.8;
      font-size: 1rem;
    }

    .product-links {
      display: flex;
      position: relative;
      margin-top: 11px;
      flex-wrap: wrap;
      gap: 4px;

      a {
        color: #fff;
        font-size: 16px;

        // text-decoration: unset;
        transition: opacity 300ms;
        flex: 100%;

        &:hover {
          opacity: 0.8;
        }
      }
    }
  }

  .history-img {
    position: relative;
    left: 30px;
    margin-left: 0;
    width: 380px;
    height: 220px;
    box-shadow: 15px 17px 40px;
    border-radius: 5px;
  }

  // animation

  .history_card {
    transform: translate3d(0, -20px, 0);
    transition: transform 400ms;

    .history-img {
        filter: grayscale(1);
        transition: all 400ms;
      }

    &.is-show {
      transform: translate3d(0, 0, 0);

      .history-img {
        filter: grayscale(0);
      }

      .history-year {
          color: #b3dcff;
      }
    }
  }

  @media all and (max-width: 1280px) and (min-width: 730.5px) {
  .history_card {
    width: 50%;

    .history-img {
      position: relative;
      width: 90%;
      height: auto;
    }

    .info-container {
      position: relative;
      padding: 13px 0;
      width: 90%;

      .history-info,
      .product-links {
        padding: 20px;
      }
    }

    &.text-left {
      margin-left: -50%;

      .history-img {
        display: block;
        margin-left: -10px;
      }

      .history-year {
        position: relative;
        right: 5%;
      }

      .history-title {
        left: calc(100% + 22px);
        margin-left: 0;
      }

      .info-container {
        left: 5%;
      }
    }

    &.text-right {
      margin-left: 0;

      .history-img {
        left: 5%;
      }

      .history-year {
        position: relative;
        left: 5%;
      }

      .history-title {
        left: -220px;
        margin-left: 0;
        width: 200px;
      }

      .info-container {
        left: 5%;
      }
    }
  }
  
}


@media all and (max-width: 730.4px) {
  .history_card {
    text-align: left !important;
    left: 43px;
    margin-left: 0 !important;
    padding-bottom: 66px;
    width: calc(100% - 66px);
    transform: none;

    .history-title {
      text-align: left !important;
      top: 0;
      left: 0;
      margin-left: 0 !important;
      width: 100%;

      &:before {
        right: unset;
        left: -21px !important;
        margin: 0;
      }
    }

    .history-info {
      text-align: left !important;
      margin-top: 0;
    }
    .history-img {
      left: 4px;
      margin-top: 60px;
      width: 100%;
      height: 100%;
    }
  }
}
</style>