<template>
  <div class="hello">
      <ul>
          <li><video id="video" width="720" height="560" autoplay muted></video></li>
          <li><button @click="takePic">Take Pic</button></li>
          <li><canvas id="captured"></canvas></li>
      </ul>
  </div>
</template>

<script>
import webCam from 'webcam-selfie-capture';

export default {
  name: 'WebcamCapture',
  props: {},
  data: function() {
	return {
		webCamInstance: null
	}
  },
  mounted() {
   let self = this
    self.webCamInstance = webCam
    self.webCamInstance.setVideoElementId('video')
    self.webCamInstance.setVideoElementEventListener()
    self.webCamInstance.loadModels()
    self.webCamInstance.startVideo()
  },
  methods: {
    takePic() {
      let self = this
      self.webCamInstance.captureSelfie('captured')
    }
  }
}
</script>

<style scoped>
</style>
