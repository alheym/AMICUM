<script>
export default {
  props: {
    image: String,
    title: String,
    notificationCount: {
      type: Number,
      default: 0,
    },
    clickHandler: Function,
  },
  methods: {
    handleClick() {
      // Вызываем событие "item-clicked" и передаем заголовок элемента
      this.$emit("item-clicked", this.title);
    },
  },
};
</script>

<template>
  <div class="action" @click="handleClick">
    <div class="action__notification" v-if="notificationCount > 0">
      {{ notificationCount }}
    </div>
    <div class="action__title">{{ title }}</div>
    <img :src="image" alt="Icon" class="action__icon" />
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.action {
  position: relative;
  cursor: pointer;
  width: calc((390px / 1920px) * 100vw);
  height: calc((300px / 1920px) * 100vw);
  background-color: $orange;
  border-radius: calc((3px / 1080px) * 100vh);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 5px 4px 7px rgba(0, 0, 0, 0.2);

  &__title {
    font-size: calc((24px / 1920px) * 100vw);
    margin: calc((30px / 1920px) * 100vw) 0;
  }

  &__icon {
    width: calc((130px / 1920px) * 100vw);
    margin-bottom: calc((30px / 1920px) * 100vw);
  }
  &__notification {
    position: absolute;
    top: calc((-30px / 1920px) * 100vw);
    right: calc((-30px / 1920px) * 100vw);
    width: calc((60px / 1920px) * 100vw);
    height: calc((60px / 1920px) * 100vw);
    border-radius: 50%;
    background-color: $notification;
    box-shadow: 5px 4px 7px rgba(0, 0, 0, 0.2);
    color: black;
    text-align: center;
    padding: calc((10px / 1920px) * 100vw);
    font-size: calc((24px / 1920px) * 100vw);
    font-weight: 600;
  }
}
</style>
