<template>
  <div class="singleButton"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <img
        src="@/assets/ui-buttons/fullscreen.svg"
        alt="fullscreen"
        v-if="fullscreen"
        @click="fullscreenSwitch"
        class="buttonImg">
    <img
        src="@/assets/ui-buttons/fullscreen_exit.svg"
        alt="fullscreen_exit"
        v-else
        @click="fullscreenSwitch"
        class="buttonImg">
    <Tooltip :title="fullscreen ? 'Fullscreen' : 'Exit'" v-show="tooltip"/>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'Fullscreen',
  components: {Tooltip},
  data() {
    return {
      fullscreen: true,
      tooltip: false,
    }
  },
  methods: {
    fullscreenSwitch() {
      this.fullscreen = !this.fullscreen;
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
