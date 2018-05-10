<template>
  <div class="" onunload="myFunction()">
    <button type="button" @click="stops">Stop</button>
    <button type="button" @click="starts">Start</button>
    {{stat}} {{time}} <br>
    <iframe id="frames" src="" height="1000" width="1000">
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
        if (vm.time === 0) {
          console.log('re')
          vm.refreshs()
        }
        if (vm.time > 0) {
          vm.time--
        } else {
          vm.time = 60
        }
      }, 1000)
    }
  },
  mounted () {
    // console.log('re')
    this.starts()
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
