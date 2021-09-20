<template>
  <div class="singleButton"
       @click="showSubtitlesHandler"
       @mouseenter="showTooltip"
       @mouseleave="hideTooltip">
    <img src="@/assets/ui-buttons/subtitles.svg" alt="play" class="buttonImg">
    <Tooltip title="Subtitles" v-show="tooltip"/>
    <div class="subtitlesTooltip" v-show="showSubtitles">
      <div class="subtitlesTooltipInner">
        <div class="subtitlesSection">
          <p class="settingsTitle">Audio</p>
          <div class="qualities leftInner">
            <div v-for="item in audio" class="qualityContainer"
                 :key="item"
                 @click="setAudio(item)"
                 :class="{ selected: doneIconAudio === item }">
              <img class="doneIcon" v-show="doneIconAudio === item" src="@/assets/ui-buttons/done.svg" alt="done"/>
              <p class="quality">{{ item }}</p>
            </div>
          </div>
        </div>
        <div class="subtitlesSection">
          <p class="settingsTitle">Subtitles</p>
          <div class="qualities rightInner">
            <div v-for="item in subtitles" class="qualityContainer"
                 :key="item"
                 @click="setSubtitles(item)"
                 :class="{ selected: doneIconSubtitles === item }">
              <img class="doneIcon" v-show="doneIconSubtitles === item" src="@/assets/ui-buttons/done.svg" alt="done"/>
              <p class="quality">{{ item }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="triangle"></div>
    </div>
  </div>
</template>

<script>
import Tooltip from "@/components/ControlButtons/Tooltip";
import '@/assets/styles.css';

export default {
  name: 'Subtitles',
  components: {Tooltip},
  data() {
    return {
      tooltip: false,
      showSubtitles: false,
      doneIconSubtitles: 'Off',
      doneIconAudio: 'Choose me',
      subtitles: ['Off', 'Arabic', 'English(CC)', 'German'],
      audio: ['Choose me', 'Arabic', 'Icelandic', 'Spanish'],
    }
  },
  methods: {
    showTooltip() {
      if (!this.tooltip && !this.showSubtitles) {
        this.tooltip = true;
      }
    },
    hideTooltip() {
      this.tooltip = false;
    },
    showSubtitlesHandler() {
      this.tooltip = false;
      this.showSubtitles = !this.showSubtitles;
    },
    setAudio(value) {
      this.doneIconAudio = value;
    },
    setSubtitles(value) {
      this.doneIconSubtitles = value;
    },
  }
}
</script>

<style>
.subtitlesTooltip {
  color: white;
  width: 300px;
  padding: 5px 0;
  background-color: #152129;
  border: 1px solid #3A444B;
  border-radius: 3px;
  position: absolute;
  top: -100%;
  left: 50%;
  transform: translate(-50%, -100%);
}
.subtitlesTooltipInner {
  display: flex;
  justify-content: space-around;
  margin-bottom: 20px;
}
.subtitlesSection {
  width: 50%;
}
.settingsTitle {
  font-weight: bold;
  margin-bottom: 15px;
  margin-left: 20px;
}
.leftInner {
  border-right-color: #3A444B;
  border-right-style: solid;
  border-right-width: 1px;
  padding-right: 30px;
}
.selected {
  color: white !important;
}
.qualities {
  width: 100%;
  padding: 0 26px 20px 0;
  text-align: left;
}
.qualityContainer {
  cursor: pointer;
  padding-left: 30px;
  color: rgba(255, 255, 255, 0.6);
  position: relative;
}
.quality {
  margin: 0 auto;
  position: relative;
}
.qualityContainer:hover {
  background-color: #3A444B;
  color: #FFFFFF;
}
</style>
