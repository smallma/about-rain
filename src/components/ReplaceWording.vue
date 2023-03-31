<script setup>
  defineProps({
    wodingList: Array
  })
</script>


<template>
  <div class="replace_wording">
    <div class="wording" 
      v-for="(i, index) of wodingList"
      v-bind:class="{ active : index === this.count }">{{ i }}</div>
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

    computed:{
      isSelected: function() {
        return function(index, count) {
          return index === count;
        }
      }
    },

    mounted() {
      setInterval(()=> {
        this.count = this.count + 1;
        if (this.count > this.wodingList.length - 1) {
          this.count = 0;
        }

        console.log(this.count);
      }, 2000);
    }
  }
  
</script>

<style lang="scss" scoped>
@keyframes wordingRotateAni {
  0% {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }

  10% {
    transform: translate3d(0, -100%, 0);
  }

  80% {
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
  overflow: hidden;
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
      animation: wordingRotateAni 2000ms forwards;
    }
  }
}
</style>