<template>
  <div class="videoContainer"
       @mouseenter="showControlsHandler"
       @mouseleave="hideControlsHandler">
    <transition name="fade">
      <TopControls v-show="showControls"/>
    </transition>
    <video
        ref="video"
        class="videoPlayer"
        :controls="false"
        :autoPlay="false"
        :poster="posterUrl"
    />
    <transition name="fade">
      <BottomControls v-show="showControls"/>
    </transition>
  </div>
</template>

<script>
import BottomControls from "@/components/BottomControls";
import TopControls from "@/components/TopControls";
import shaka from 'shaka-player';

export default {
  name: 'Player',
  components: {BottomControls, TopControls},
  props: {
    manifestUrl: {
      type: String,
      required: true
    },
    licenseServer: {
      type: String,
      required: true
    },
    posterUrl: {
      type: String,
      required: false,
      default: ''
    }
  },
  data() {
    return {
      player: null,
      playing: false,
      showControls: false,

    };
  },
  mounted() {
    this.player = new shaka.Player(this.$refs.video);
    this.player
        .load(this.manifestUrl)
        .then(() => {
          console.log('The video has now been loaded!');
        })
        .catch(this.onError);
  },
  methods: {
    showControlsHandler() {
      this.showControls = true;
    },
    hideControlsHandler() {
      this.showControls = false;
    },
    onError(error) {
      console.error('Error code', error.code, 'object', error);
    },
  },
}
</script>

<style>
.videoContainer {
  width: 1000px;
  height: auto;
  margin: 50px auto;
  position: relative;
}

.videoPlayer {
  width: 100%;
  outline: none;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .7s;
}
.fade-enter, .fade-leave-to  {
  opacity: 0;
}
</style>
