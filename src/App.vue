<template>
  <Home/>
</template>

<script>
import Home from './pages/Home'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}

html {
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
}

body {
  height: 100%;
  &::-webkit-scrollbar {
    width: 8px;
  }

  &::-webkit-scrollbar-thumb {
    min-height: 25px;
    background-color: rgb(202, 203, 203);
    border-radius: 15px;
  }

  &::-webkit-scrollbar-track {
    background-color: rgb(237, 238, 238);
  }
}


</style>
<style src="./assets/css/index.css"></style>

