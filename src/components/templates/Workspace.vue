<script setup></script>

<template>
  <section class="workspace">
    <div class="workspace__logo"></div>
    <div class="workspace__actions">
      <div class="workspace__actions-item">Начать работу</div>
      <div class="workspace__actions-item">Уведомления</div>
      <div class="workspace__actions-item">Обучение</div>
      <div class="workspace__actions-item">Достижения</div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.workspace {
  padding: 10px;
  width: 100%;
  display: flex;
  flex-direction: column;

  &__logo {
    width: 80px;
    height: 30px;
    background-color: yellow;
  }

  &__actions {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 10px;
    align-items: center;
    justify-content: center;

    &-item {
      background-color: $orange;
      border-radius: 3px;
    }
  }
}
</style>
