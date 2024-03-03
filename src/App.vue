<template>
  <header class="title">
    <img src="./img/logo.png" class="title__img">
  </header>
  <HelloWorld />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Verdana, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding-left: 50px;
}

.title {
  position: relative;
  display: flex;
  justify-content: center;
  height: 100px;
  margin-top: 20px;
  margin-bottom: 50px;
}

.title__img {
  position: absolute;
  left: 55px;
  top: 0;
  height: 100px;
}
</style>
