<template>
  <div id="portfolio">
    <div class="center_line"></div>

    <HistoryCard 
      v-for="history in historys"
      :history="history"
      :key="history.id"
    />

  </div>
</template>

<script>
  import HistoryCard from './HistoryCard.vue'

  export default {
    name: 'Profolio',
    components: {
      HistoryCard
    },
    data () {
      return {
        historys: [
          {
            'id': 1,
            'type': 'education',
            'from': 'ntut',
            'year': '1991',
            'title': 'Graduated from NUTU',
            'info': 'test'
          },
          {
            'id': 2,
            'type': 'Project',
            'from': 'Quanta',
            'year': '1991',
            'title': 'Quanta - Prpject 1',
            'info': 'test'
          },
          {
            'id': 3,
            'type': 'Project',
            'from': 'ASUS',
            'year': '1991',
            'title': 'ASUS - Prpject 1',
            'info': 'test'
          }
        ]
      }
    }
  }
</script>

<style lang="scss" scoped>
#portfolio {
  position: relative;
  display: block;
  padding-top: 168px;

  min-height: 100vh;
  background: rgba(99, 99, 99, 0.8);
}
.center_line {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 4px;
  height: 100%;
  background-color: #7f7f7f;
}
</style>



