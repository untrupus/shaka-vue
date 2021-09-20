<template>
  <div class="singleButton"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <img src="@/assets/ui-buttons/forward_10.svg" alt="play" class="buttonImg">
    <Tooltip title="Forward" v-show="tooltip"/>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'Forward',
  components: {Tooltip},
  data() {
    return {
      tooltip: false,
    }
  },
  methods: {
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
