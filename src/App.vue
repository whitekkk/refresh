<template>
  <div onunload="myFunction()" width="1000" height="1000" z-index="999">
    <button type="button" @click="stops" id="test">Stop</button>
    <button type="button" @click="starts">Start</button>
    {{stat}} {{time}} <br>
    <iframe id="frames" src="http://10.4.15.222" height="1000" width="1000" @click="mousePosition()">
      <!-- <meta http-equiv="refresh" :content="stop" > -->
    </iframe>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

window.onbeforeunload = function () {
  return 'Noo!'
}

export default {
  name: 'App',
  data () {
    return {
      stop,
      stat: 'running',
      time: 60
    }
  },
  components: {
    HelloWorld
  },
  methods: {
    refreshs () {
      var frame = document.getElementById('frames')
      frame.src = frame.src
      this.stat = 'running'
    },
    stops () {
      window.clearInterval(this.stop)
      this.stat = 'pause'
    },
    starts () {
      var vm = this
      this.stop = setInterval(function () {
        vm.refreshs()
      }, 10)
    },
    mousePosition () {
      // let vm = this
      let position = window.event
      console.log(position.clientX)
      console.log(position.clientY)
    }
  },
  mounted () {
    // console.log('re')
    this.starts()
    // simulate(document.getElementById('frames'), 'click', { pointerX: 100, pointerY: 300 })
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
