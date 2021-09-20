<template>
  <div class="topControls">
    <h3 class="topTitle">Title of Movie</h3>
    <img src="@/assets/ui-buttons/arrow_back.svg" alt="back" class="arrowBack">
  </div>
</template>

<script>
export default {
  name: 'TopControls',
  data() {
    return {}
  }
}
</script>

<style>
.topControls {
  position: absolute;
  width: 100%;
  top: 0;
  background-color: rgba(20, 20, 20, 0.3);
  height: 45px;
  justify-content: center;
  align-items: center;
  z-index: 100;
  display: flex;
}

.topTitle {
  color: white;
}

.arrowBack {
  position: absolute;
  left: 20px;
}
</style>
