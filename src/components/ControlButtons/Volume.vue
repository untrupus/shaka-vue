<template>
  <div class="volumeButton"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <div class="singleButton">
      <img
          src="@/assets/ui-buttons/volume_up.svg"
          alt="volume_up"
          v-if="mute"
          @click="volumeSwitch"
          class="buttonImg">
      <img
          src="@/assets/ui-buttons/volume_off.svg"
          alt="volume_up"
          v-else
          @click="volumeSwitch"
          class="buttonImg">
      <Tooltip :title="mute ? 'Mute' : 'On'" v-show="tooltip"/>
    </div>
    <transition name="bounce">
      <input
          class="volumeBar"
          type="range"
          step="any"
          min="0"
          max="1"
          v-show="showVolumeBar"
          v-bind:value="volume"
          v-bind:style="{
          background: 'linear-gradient(to right, rgb(204, 204, 204) '
      + volume * 100 + '%, rgb(0, 0, 0) '
      + volume * 100 + '%, rgb(0, 0, 0) 100%)'
      }"
          @change="onVolumeChange"
      />
    </transition>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'Volume',
  components: {Tooltip},
  data() {
    return {
      mute: true,
      tooltip: false,
      showVolumeBar: false,
      volume: 0.7
    }
  },
  methods: {
    volumeSwitch() {
      this.mute = !this.mute;
      this.volume = 0;
    },
    showTooltip() {
      this.tooltip = true;
      this.showVolumeBar = true;
    },
    hideTooltip() {
      this.tooltip = false;
      this.showVolumeBar = false;
    },
    onVolumeChange(event) {
      if (event.target && event.target.value) {
        this.volume = event.target.value;
      }
    },
  }
}
</script>

<style>
.volumeButton {
  display: flex;
  align-items: center;
}

.volumeBar {
  display: flex;
  height: 4px;
  margin: 0 10px 5px;
  padding: 0;
  -webkit-appearance: none;
  outline: none;
  min-width: 15px;
  max-width: 70px;
  cursor: pointer;
}

.volumeBar::-ms-track,
.volumeBar::-ms-fill-lower,
.volumeBar::-ms-fill-upper {
  background-color: transparent;
  outline: none;
}

.volumeBar::-moz-range-track {
  background-color: transparent;
  outline: none;
}

.volumeBar::-webkit-slider-thumb {
  -webkit-appearance: none;
  background-color: white;
  outline: none;
}

.volumeBar::-webkit-slider-thumb {
  width: 12px;
  height: 12px;
  border-radius: 12px;
}

.volumeBar::-moz-range-thumb {
  width: 12px;
  height: 12px;
  border-radius: 12px;
}

.volumeBar::-ms-thumb {
  width: 12px;
  height: 12px;
  border-radius: 12px;
}

.bounce-enter-active {
  animation: bounce-in .3s;
}

.bounce-leave-active {
  animation: bounce-in .3s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scaleX(0);
  }
  100% {
    transform: scaleX(1);
  }
}
</style>
