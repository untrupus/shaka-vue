<template>
  <div class="singleButton"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <img
        src="@/assets/ui-buttons/play.svg"
        alt="play"
        v-if="play"
        @click="playSwitch"
        class="buttonImg">
    <img
        src="@/assets/ui-buttons/pause.svg"
        alt="pause"
        v-else
        @click="playSwitch"
        class="buttonImg">
    <Tooltip :title="play ? 'Play' : 'Pause'" v-show="tooltip"/>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'PlayButton',
  components: {Tooltip},
  data() {
    return {
      play: true,
      tooltip: false,
    }
  },
  methods: {
    playSwitch() {
      this.play = !this.play;
    },
    showTooltip() {
      this.tooltip = true;
    },
    hideTooltip() {
      this.tooltip = false;
    }
  }
}
</script>

<style>

</style>
