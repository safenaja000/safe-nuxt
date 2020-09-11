<template>
  <div id="app">
    <div>
      <video ref="video" id="video" width="640" height="480" autoplay></video>
    </div>
    <div>
      <button id="snap" v-on:click="capture()">Snap Photo</button>
    </div>
    <canvas ref="canvas" id="canvas" width="640" height="480"></canvas>
      <img v-bind:src="captures" height="50" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      video: {},
      canvas: {},
      captures: '',
    }
  },
  mounted() {
    this.video = this.$refs.video
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
      navigator.mediaDevices.getUserMedia({ video: true }).then((stream) => {
        this.video.srcObject = stream
        this.video.play()
      })
    }
  },
  methods: {
    capture() {
      this.canvas = this.$refs.canvas
      var context = this.canvas
        .getContext('2d')
        .drawImage(this.video, 0, 0, 640, 480)
      this.captures = canvas.toDataURL('image/png')
      // console.log(this.captures)
      let data = new FormData()
      data.append('xxxxxxxxxxxxx',this.captures)
      console.log('data',data)
    },
  },
}
</script>

<style>
</style>
