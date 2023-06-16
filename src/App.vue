<script setup>
import Profile from "./components/templates/Profile.vue";
import Workspace from "./components/templates/Workspace.vue";
</script>

<template>
  <div class="is-grid">
    <div class="wrapper">
      <div class="column-item">123</div>
    </div>
  </div>
  <main class="main">
    <Profile />
    <Workspace />
  </main>
</template>

<style lang="scss" scoped>
@import "./assets/styles/main";

.is-grid::after {
  content: "";
  position: absolute;
  z-index: 1000;
  top: 0;
  bottom: 0;
  opacity: 0.15;
  left: $grid_margin;
  right: $grid_margin;
  background: repeating-linear-gradient(
    90deg,
    $grid_color 0,
    $grid_color $grid_width,
    transparent $grid_width,
    transparent $grid_width + $grid_gutter
  );
  pointer-events: none;
}

.wrapper {
  // margin: 0 $grid-margin; //отступ от края
}

.column-item {
  height: 100vh;
  background: grey;
  // width: percentage(727 / 1840);
  width: $grid_width * 4 + $grid_gutter * 3;
}

.main {
  display: flex;
  min-height: 100vh;
  width: 100%;
}
</style>
