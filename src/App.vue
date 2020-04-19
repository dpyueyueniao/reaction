<template>
  <div id="app">
    <HelloWorld msg="来测试以下反应速度吧"/>
  </div>
</template>

<script>
import HelloWorld from './views/Home.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
@import './assets/base.less';
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
* {
  margin: 0;
  padding: 0;
}
</style>
