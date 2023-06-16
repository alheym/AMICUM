<script setup>
import Profile from "./components/templates/Profile.vue";
import Workspace from "./components/templates/Workspace.vue";
</script>

<template>
  <main class="main">
    <Profile />
    <Workspace />
  </main>
</template>

<style lang="scss" scoped>
@import "./assets/styles/main";

.main {
  display: flex;
  min-height: 100vh;
  width: 100%;
}
</style>
