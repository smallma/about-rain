<script setup>
  import Header from './components/Header.vue'
  import Introduce from './components/Introduce.vue'
  import Portfolio from './components/Portfolio.vue'
  import Footer from './components/Footer.vue'
</script>

<template>
  <Header />
  <Introduce />
  <Portfolio />
  <Footer />
</template>

<style>
html {
  overflow-x: clip;
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

h1, h2, h3 {
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
  font-weight: unset;
}
</style>
