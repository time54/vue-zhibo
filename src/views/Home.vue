<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <video id="myvideo" @click="click" controls = "true" height="500" width="auto"></video>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import flvjs from 'flv.js/dist/flv.min'

export default {
  name: 'Home',
  components: {
    HelloWorld
  },
  mounted() {
    if (flvjs.isSupported()) {
      var videoElement = document.getElementById('myvideo')
      var flvPlayer = flvjs.createPlayer({
        type: 'mp4',
        url: 'http://khtest.10jqka.com.cn/dev/taojinchao/TEST/movie.mp4'
      })
      flvPlayer.attachMediaElement(videoElement)
      flvPlayer.load()
    }
  },
  methods: {
    click() {
      if (this.playing) {
        this.player.pause()
        this.playing = false
      } else {
        this.player.play()
        this.playing = true
      }
    }
  }
}
</script>
