<template>
  <div class="bottomControls">
    <div class="seekBarContainer">
      <input
          class="seekBar"
          type="range"
          step="any"
          min="0"
          v-bind:max="duration"
          v-bind:value="currentTime"
          @change="onSeekChange"
          v-bind:style="{
        background: 'linear-gradient(to right, rgb(255, 0, 0) '
          + currentTime * 100 + '%, rgb(0, 0, 0) '
          + currentTime * 100 + '%, rgb(0, 0, 0) 100%)'
       }"
      />
    </div>
    <div class="buttons">
      <div class="buttonsSection buttonsLeft">
        <PlayButton/>
        <Back10/>
        <Forward10/>
        <Volume/>
      </div>
      <div class="buttonsSection buttonsRight">
        <Subtitles/>
        <Quality/>
        <Cast/>
        <Airplay/>
        <Fullscreen/>
      </div>
    </div>
  </div>
</template>

<script>
import PlayButton from "@/components/ControlButtons/PlayButton";
import Back10 from "@/components/ControlButtons/Back10";
import Forward10 from "@/components/ControlButtons/Forward10";
import Volume from "@/components/ControlButtons/Volume";
import Subtitles from "@/components/ControlButtons/Subtitles";
import Airplay from "@/components/ControlButtons/Airplay";
import Cast from "@/components/ControlButtons/Cast";
import Fullscreen from "@/components/ControlButtons/Fullscreen";
import Quality from "@/components/ControlButtons/Quality";

export default {
  name: 'BottomControls',
  components: {
    PlayButton,
    Back10,
    Forward10,
    Volume,
    Subtitles,
    Cast,
    Airplay,
    Fullscreen,
    Quality,
  },
  data() {
    return {
      duration: 1,
      currentTime: 0,
    }
  },
  methods: {
    onSeekChange(event) {
      if (event.target && event.target.value) {
        this.currentTime = event.target.value;
      }
    },
  }
}
</script>

<style>
.bottomControls {
  position: absolute;
  width: 100%;
  bottom: 5px;
  background-color: rgba(20, 20, 20, 0.5);
  height: 45px;
  z-index: 100;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.buttons {
  margin: 5px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.buttonsSection {
  display: flex;
  margin: 0;
}

.seekBar {
  width: 100%;
  cursor: pointer;
  border-radius: 0;
  display: flex;
  height: 3px;
  margin: 0 12px 0 0;
  padding: 0;
  -webkit-appearance: none;
  outline: none;
}
.seekBar::-webkit-slider-thumb {
  width: 12px;
  height: 12px;
  border-radius: 7px;
  -webkit-appearance: none;
  background-color: red;
  box-shadow: 1px 1px 1px rgba(50, 50, 50, 0.75);
}
</style>
