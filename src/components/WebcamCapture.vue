<template>
    <v-container>
        <v-row no-gutters class="header">
            <v-col cols="12" sm="12">
                <v-card
                    class="pa-2"
                    outlined
                    tile
                >
                    Webcam Selfie Capture Demo
                </v-card>
            </v-col>
        </v-row>
        <v-row no-gutters class="content">
            <v-col cols="6" sm="6" class="webcam-container">
                <v-card
                    class="pa-2"
                    outlined
                    tile
                >
                    <v-card-title>Your live feed</v-card-title>
                    <video id="video-feed" width="660" height="480" autoplay muted></video>
                </v-card>
            </v-col>
            <v-col cols="6" sm="6" class="selfie-container">
                <v-card
                    class="pa-2"
                    outlined
                    tile
                >
                    <v-card-title>Your captured pic</v-card-title>
                    <canvas id="captured"></canvas>
                </v-card>
            </v-col>
        </v-row>
        <v-row no-gutters class="footer">
            <v-col cols="12" sm="12">
                <v-card
                    class="pa-2"
                    outlined
                    tile
                >
                    <v-card-actions>
                        <v-btn x-large color="success" @click="takePic" dark>Capture</v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
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
    self.webCamInstance.setVideoElementId('video-feed')
	self.webCamInstance.loadModels()
    self.webCamInstance.setVideoElementEventListener()
  },
  methods: {
    takePic() {
      let self = this
      self.webCamInstance.captureSelfie('captured')
    }
  }
}
</script>

<style scoped lang="scss">
    .container {
        width: 100%;
        max-width: 100vw;
        padding: unset;
    }
    .footer,
    .header {
        height: 10vh;
        width: 100vw;

        .v-card {
            background: #292929;
            color: #E2E2E2;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 32px;
            font-weight: 900;

            .v-card__actions {
                .v-btn {
                    background: #131313 !important;
                }
            }
        }
    }
    .content {
        height: 80vh;

        .v-card {
            height: 80%;
            width: 80%;
            display: flex;
            flex-flow: column;
            justify-content: center;
            align-items: center;
        }

        .selfie-container,
        .webcam-container {
            display: flex;
            justify-content: center;
            align-items: center;
            border: 2px solid #131313;
            background: #292929;

            .v-card {
                background: #131313;
                .v-card__title {
                    color: #979797;
                }
            }
        }
    }
</style>
