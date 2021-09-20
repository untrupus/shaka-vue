<template>
  <div id="app">
    <Player
        :license-server="licenseServer"
        :manifest-url="manifestUrl"
        :poster-url="posterUrl"
    />
  </div>
</template>

<script>
import Player from "@/components/Player";

export default {
  name: 'App',
  components: {Player},
  data() {
    return {
      licenseServer: 'https://widevine-proxy.appspot.com/proxy',
      manifestUrl:
          'https://dash.akamaized.net/dash264/TestCases/1c/qualcomm/2/MultiRate.mpd',
      posterUrl:
          'https://upload.wikimedia.org/wikipedia/commons/a/a7/Big_Buck_Bunny_thumbnail_vlc.png'
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
