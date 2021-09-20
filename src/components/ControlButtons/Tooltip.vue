<template>
  <div class="tooltip">
    <span>{{ title }}</span>
    <div class="triangle"></div>
  </div>
</template>

<script>
export default {
  name: 'Tooltip',
  props: ['title'],
  data() {
    return {

    }
  }
}
</script>

<style>
.tooltip {
  color: white;
  padding: 5px;
  background-color: #152129;
  position: absolute;
  top: -40px;
  left: 50%;
  transform: translate(-50%, 0);
}
.triangle {
  position: absolute;
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 7px 7px 0 7px;
  border-color: #152129 transparent transparent transparent;
  left: 50%;
  transform: translate(-50%, -5px);
  bottom: -10px;
}
</style>
