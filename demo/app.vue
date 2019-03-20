<style lang="scss">
  .toggle {
    cursor: pointer;
    margin: 20px;
  }
</style>

<style lang="scss">

#wrapper{
  display:flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
</style>

<template>
  <div class="row" id="wrapper">
    <!-- <div class="toggle" @click="toggle">TOGGLE</div> -->

    <audio-recorder v-if="showRecorder"
      upload-url="some url"
      :attempts="3"
      :time="1"
      :headers="headers"
      :before-recording="callback"
      :pause-recording="callback"
      :after-recording="callback"
      :after-cancel="cancel"
      :select-record="callback"
      :before-upload="callback"
      :loadingIcon="false"
      :successful-upload="callback"
      :failed-upload="callback"
      :bit-rate="192"/>

    <audio-player :src="mp3" v-if="!showRecorder"/>
  </div>
</template>

<script>
  export default {
    name: 'app',
    data () {
      return {
        mp3: '/demo/example.mp3',
        showRecorder: true,
        headers: {
          'X-Custom-Header': 'some data'
        }
      }
    },
    methods: {
      callback (msg) {
        console.log('Event: ', msg)
      },
      cancel () {
        console.log('Canceled ')
      },
      toggle () {
        this.showRecorder = !this.showRecorder
      }
    }
  }
</script>
