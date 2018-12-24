<template>
  <div>
    <canvas id="canvas" width="960" height="480"></canvas>
  </div>
</template>

<script>
export default {
  // name: 'HelloWorld',
  data () {
    return {
      // msg: 'Welcome to Your Vue.js App'
      gameWidth: 960,
      gameHeight: 480,
      cjs: null,
      canvas: null,
      stage: null
    }
  },

  mounted () {
    this.init()
  },
  methods: {
    init () {
      this.cjs = window.createjs
      this.canvas = document.getElementById('canvas')
      this.stage = new this.cjs.Stage(this.canvas)
      var backGround = this.bgLayer()
      this.stage.addChild(backGround)
      this.cjs.Ticker.setFPS(40)
      this.cjs.Ticker.addEventListener('tick', this.stage)
      // this.cjs.Ticker.addEventListener('tick', this.tick)
      var uiLayer = this.uiLayer()
      var cityLayer = this.cityLayer()
      this.stage.addChild(uiLayer)
      this.stage.addChild(cityLayer)
    },
    tick () {
      this.stage.update()
    },
    layer () {
      var obj = new this.cjs.Container()
      return obj
    },
    cityLayer () {
      var obj = this.layer()
      return obj
    },
    bgLayer () {
      var layer = this.layer()
      var bitmap = new this.cjs.Bitmap('../../static/images/bg.png')
      layer.addChild(bitmap)

      var cloud1 = new this.cjs.Bitmap('../../static/images/cloud1.png')
      cloud1.y = 30
      cloud1.alpha = 0.4
      layer.addChild(cloud1)

      this.cjs.Tween.get(cloud1, {loop: true}).to({x: this.gameWidth + 300}, 0).wait(15500).to({x: -300}, 50 * 1000)

      var cloud2 = new this.cjs.Bitmap('../../static/images/cloud2.png')
      cloud2.y = 300
      cloud2.alpha = 0.4
      layer.addChild(cloud2)
      this.cjs.Tween.get(cloud2, {loop: true}).to({x: this.gameWidth + 50}, 0).wait(500).to({x: -300}, 50 * 1000)
      return layer
    },
    uiLayer () {
      var obj = this.layer()
      this.setupHUD(obj)
      return obj
    },
    placeBitmap (layer, path, x, y) {
      var bitmap = new this.cjs.Bitmap(path)
      bitmap.x = x
      bitmap.y = y
      layer.addChild(bitmap)
    },
    placeText (layer, textStr, size, x, y, align) {
      var text = new this.cjs.Text(textStr, size + 'px Arial', '#222')

      text.x = x
      text.y = y
      text.textAlign = align
      layer.addChild(text)
      return text
    },
    setupHUD (layer) {
      this.placeBitmap(layer, '../..' +
        '/static/images/candies.png', 28, 16)
      this.placeBitmap(layer, '../..' +
        '/static/images/diamonds.png', 154, 14)
      this.placeBitmap(layer, '../../static/images/populations.png', 810, 14)

      this.consIndicator = this.placeText(layer, '12345', 12, 123, 34, 'right')
      this.diamondsIndicator = this.placeText(layer, '0', 12, 250, 34, 'right')
      this.populationIndicator = this.placeText(layer, '100', 16, 845, 32, 'center')
    }
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
</style>
