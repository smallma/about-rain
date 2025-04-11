<script setup>
  defineProps({
    wodingList: Array
  })
</script>


<template>
  <div class="replace_wording">
    <div class="wording" 
      v-for="(i, index) of wodingList"
      :class="{ active : isSelected(index)}">{{ i }}</div>
  </div>
</template>

<script>
  export default {
    name: 'ReplaceWording',
    data() {
      return {
        count: 0
      }
    },
    mounted() {
      setInterval(()=> {
        this.count = this.count + 1;
        if (this.count > this.wodingList.length - 1) {
          this.count = 0;
        }
      }, 3000);
    },
    methods: {
      isSelected: function(index) {
        return index === this.count;
      }
    }
  }
  
</script>

<style lang="scss" scoped>
@keyframes wordingRotate {
  0% {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }

  25% {
    transform: translate3d(0, -100%, 0);
  }

  60% {
    transform: translate3d(0, -100%, 0);
  }

  97% {
    opacity: 1;
    transform: translate3d(0, -200%, 0);
  }

  98% {
    opacity: 0;
    transform: translate3d(0, -200%, 0);
  }

  99% {
    opacity: 0;
    transform: translate3d(0, 0, 0);
  }

  100% {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.replace_wording {
  display: inline-block;
  position: relative;
  overflow: clip;
  width: 300px;
  height: 4rem;

  .wording {
    position: absolute;
    top: 100%;
    opacity: 1;
    color: #fff;
    font-size: 3rem;
    transform: translate3d(0, 0, 0);
    
    &.active {
      animation: wordingRotate 3000ms forwards;
    }
  }
}
</style>