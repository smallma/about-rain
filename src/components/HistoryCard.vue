<template>
  <div :class="'history_card ' + getAlign(history.id) + ' ' + isShow">
    <!-- <img class="history-img" v-bind:src="'@/assets/images/' + history.type + '/' + history.from + '/history_img.jpg'" /> -->
    <!-- <img class="history-img" :src="require(`../../assets/images/${history.type}/${history.from}/history_img.jpg`)" /> -->
    <img class="history-img" v-bind:src="'/images/' + history.type + '/' + history.from + '/history_img.jpg'" />
    <span class="history-year">{{ history.year }}</span>
    <span class="history-info">{{ history.info }}</span>
    <span class="history-title">{{ history.title }}</span>
  </div>
</template>

<script>
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
        scrollTime: new Date().getTime(),
        isShow: '',
        windowHeight: window.innerHeight,
        bgClass: 'width-first'
      };
    },
    created () {
      window.addEventListener('scroll', this.handleScroll);

      this.bgClass = this.history.bgHeightFull ? 'height-first' : 'width-first';
    },
    destroyed () {
      window.removeEventListener('scroll', this.handleScroll);
    },
    mounted () {
      const getOffset = (element, horizontal = false) => {
        if(!element) { return 0; }
        return getOffset(element.offsetParent, horizontal) + (horizontal ? element.offsetLeft : element.offsetTop);
      }

      this.offsetTop = getOffset(this.$el);
    },
    methods: {
      getAlign: function(id) {
        const align = id % 2 == 0 ? 'left' : 'right';
        return 'text-' + align;
      },
      handleScroll (event) {
        const currentTime = new Date().getTime();

        if (currentTime - this.scrollTime < 100) { return;}
        // console.log('this.scrollTime: ', this.scrollTime, ', currentTime: ', currentTime);
        this.scrollTime = currentTime;

        const windowBottom = window.scrollY + this.windowHeight;
        const rangeTop = this.windowHeight * 0.7;
        const rangeBottom = this.windowHeight * 0.3;
        // console.log(window.scrollY, this.offsetTop, this.windowHeight, this.offsetTop + rangeTop, this.offsetTop + rangeBottom);
        if (windowBottom > this.offsetTop + rangeBottom && windowBottom < this.offsetTop + rangeTop) {
          const backgroundSrc = '/images/' + this.history.type + '/' + this.history.from + '/history_bg.jpg';
          this.isShow = ' is-show';

          if (window.backgroundSrc === backgroundSrc) {return; }
          window.backgroundSrc = backgroundSrc;
          console.log('backgroundSrc: ', backgroundSrc, this.bgClass);
          this.$emit('changeBackground', backgroundSrc, this.bgClass);
        } else {
          this.isShow = '';
        }
      }
    }
  }
</script>


<style lang="scss" scoped>
  .history_card {
    position: relative;
    left: 50%;

    width: 440px;
    padding-bottom: 100px;

    &.text-right {
      text-align: left;
      margin-left: 50px;
      .history-title {
        text-align: right;
        margin-left: -890px;

        &:before {
          right: -22px;

        }
      }

      .history-year{
        text-align: left;
      }
    }

    &.text-left {
      text-align: right;
      margin-left: -490px;

      .history-title {
        text-align: left;
        margin-left: 292px;
        &:before {
          left: -24px;
        }
      }
    }

    .history-year,
    .history-info {
      position: relative;
      display: block;
      color: #fff;
    }

    .history-year {
      font-size: 50px;
      font-weight: bold;
      margin-top: -41px;
      margin-left: 11px;
      text-shadow: 1px 2px 5px #333;
    }

    .history-info {
      margin-top: 8px;
      line-height: 1.8;
      font-size: 1rem;
      padding: 13px 13px;
      background: rgba(0,0,0,0.4);
      border-radius: 5px;
    }

    .history-title {
      position: absolute;
      display: block;
      width: 600px;
      color: #fff;

      // top: 50%;
      top: 90px;
      left: 50%;

      &:before {
        position: absolute;
        display: block;
        content: '';
        top: 50%;
        width: 4px;
        height: 15px;
        background: rgba(255, 255, 255, 0.5);
        transform: translateY(-50%);
      }
    }
  }
  .history-img {
    margin-left: 0;
    width: 380px;
    height: 220px;

    box-shadow: 15px 17px 40px;
    border-radius: 5px;
  }

  // animation

  .history_card {
    transform: translate3d(0px, -20px, 0px);
    transition: transform 400ms;

     .history-img {
        filter: grayscale(1);
        transition: all 400ms;
      }
    &.is-show {
      
      transform: translate3d(0px, 0px, 0px);
      .history-img {
        filter: grayscale(0);
      }
    }
  }
</style>