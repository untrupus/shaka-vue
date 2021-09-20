<template>
  <div class="singleButton"
       @click="showSettingsHandler"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <img src="@/assets/ui-buttons/settings.svg" alt="play" class="buttonImg">
    <Tooltip title="Quality" v-show="tooltip"/>
    <div class="settingsTooltip" v-show="showSettings">
      <p class="settingsTitle">Video Quality</p>
      <div class="qualities">
        <div class="qualityContainer"
             v-for="item in qualities"
             :key="item.rate"
             @click="setQuality(item.rate)"
             :class="{ selected: doneIcon === item.rate }">
          <img class="doneIcon" v-show="doneIcon === item.rate" src="@/assets/ui-buttons/done.svg" alt="done"/>
          <p class="quality">{{ item.rate }}<span class="hd">{{ item.chip }}</span></p>
        </div>
        <div class="triangle"></div>
      </div>
    </div>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'Quality',
  components: {Tooltip},
  data() {
    return {
      tooltip: false,
      showSettings: false,
      doneIcon: 'Auto',
      qualities: [
        {
          rate: '2160', chip: '4k',
        },
        {
          rate: '1440', chip: 'HD',
        },
        {
          rate: '1080', chip: 'HD',
        },
        {
          rate: '480', chip: '',
        },
        {
          rate: '240', chip: '',
        },
        {
          rate: 'Auto', chip: '',
        },
      ],
    }
  },
  methods: {
    showTooltip() {
      if (!this.tooltip && !this.showSettings) {
        this.tooltip = true;
      }
    },
    hideTooltip() {
      this.tooltip = false;
    },
    showSettingsHandler() {
      this.tooltip = false;
      this.showSettings = !this.showSettings;
    },
    setQuality(value) {
      this.showSettings = false;
      this.doneIcon = value;
    },
  }
}
</script>

<style>
.settingsTitle {
  font-weight: bold;
  margin-bottom: 5px;
  font-size: 16px;
}
.qualities {
  width: 100%;
  padding: 0;
  text-align: left;
  font-size: 14px;
}
.qualityContainer {
  cursor: pointer;
  padding-left: 50px;
  color: rgba(255, 255, 255, 0.6);
  position: relative;
}
.qualityContainer:hover {
  background-color: #3A444B;
  color: #FFFFFF;
}
.quality {
  margin: 0 auto;
  position: relative;
}
.hd {
  position: absolute;
  color: tomato;
  font-size: 10px;
  margin-left: 5px;
  font-weight: bold;
  top: 0;
}
.selected {
  color: white !important;
}
.settingsTooltip {
  color: white;
  width: 150px;
  text-align: center;
  padding: 5px 0 20px;
  background-color: #152129;
  border: 1px solid #3A444B;
  border-radius: 3px;
  position: absolute;
  top: -100%;
  left: 50%;
  transform: translate(-50%, -100%);
}

</style>
