<template>
  <div id="app">
    <!--
    <img src="./assets/logo.png">
    <router-view/>
    -->
<game-container></game-container>
  </div>
</template>

<script>
import GameContainer from './components/gamecontainer'
export default {
  // name: 'App'
  name: 'app',
  components: {
    GameContainer
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
