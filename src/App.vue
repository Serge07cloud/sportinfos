<template>
  <div id="app">
    <sports/>
  </div>
</template>

<script>
import sports from '@/components/sports.vue'
export default {
  name: 'App',
  components: {
    sports
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
