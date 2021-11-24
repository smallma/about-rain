<template>
  <div :class="'history_card ' + getAlign(history.id) ">
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
    methods: {
      getAlign: function(id) {
        const align = id % 2 == 0 ? 'left' : 'right';
        return 'text-' + align;
      }
    }
  }
</script>


<style lang="scss" scoped>
  .history_card {
    position: relative;
    left: 50%;

    width: 500px;
    margin-bottom: 100px;

    &.text-right {
      text-align: left;
      margin-left: 40px;
      .history-title {
        text-align: right;
        margin-left: -910px;

        &:before {
          right: -22px;

        }
      }

      .history-year,
      .history-info {
        text-align: left;
      }
    }

    &.text-left {
      text-align: right;
      margin-left: -540px;

      .history-title {
        text-align: left;
        margin-left: 312px;
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
    }

    .history-info {
      margin-top: 8px;
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
    width: 310px;
    height: 180px;
  }
</style>