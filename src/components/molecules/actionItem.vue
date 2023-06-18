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
  width: 20.31vw;
  height: 15.62vw;
  background-color: $orange;
  border-radius: 0.28vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: 0.26vw 0.2vw 0.36vw rgba(0, 0, 0, 0.3);
  transition: transform 0.3s;

  &:hover {
    transform: scale(1.05);
  }

  &__title {
    font-size: $f24;
    margin: 1.56vw 0;
  }

  &__icon {
    width: 6.77vw;
    margin-bottom: 1.56vw;
  }
  &__notification {
    display: flex;
    align-items: center;
    justify-content: space-around;
    position: absolute;
    top: -1.56vw;
    right: -1.56vw;
    width: 3.12vw;
    height: 3.12vw;
    border-radius: 50%;
    background-color: $notification;
    box-shadow: 0.26vw 0.2vw 0.36vw rgba(0, 0, 0, 0.3);
    color: black;
    font-size: $f24;
    font-weight: 600;
  }
}
</style>
