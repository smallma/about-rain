<script setup>
  import Header from './components/Header.vue'
  import Introduce from './components/Introduce.vue'

  import Footer from './components/Footer.vue'
</script>

<template>
  <Header />
  <Introduce />
  <Footer />
</template>

<style>
html {
  width: 100%;
  font-size: 16px;
  background: #1d1b1d;
}

body {
  margin: 0;
}

#app {
  display: block;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
