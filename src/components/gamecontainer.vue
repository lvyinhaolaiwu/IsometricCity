<template>
  <div>
<header>
  <div class="row">
    <h1>Isometric City</h1>
  </div>
</header>
    <section id="game" class="row">
<game-scene></game-scene>
    </section>
  </div>
</template>

<script>
import GameScene from './gamescenecomponent'
export default {
  /* name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
  */
  components: {
    GameScene
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  /*
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
*/
#game{
  position: relative;
  width: 960px;
  height: 480px;
  border: 1px solid black;
}
</style>
