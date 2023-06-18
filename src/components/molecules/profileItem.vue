<script>
import ProgressBar from "../atoms/progressBar.vue";
export default {
  components: {
    ProgressBar,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    class: {
      type: String,
      default: "",
    },
    progress: {
      type: Number,
      required: true,
    },
    score: {
      type: String,
      default: "",
    },
    descr: {
      type: String,
      default: "",
    },
    color: {
      type: String,
      default: "#add919",
    },
  },
  methods: {
    handleClick() {
      this.$emit("item-clicked", this.title);
    },
  },
};
</script>

<template>
  <div class="progress__item" @click="handleClick">
    <div class="progress__item-title">{{ title }}</div>
    <ProgressBar
      :class="class"
      :progress="progress"
      :score="score"
      :descr="descr"
      :color="color"
    />
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.progress__item {
  padding: 0 3.12vw 1.04vw;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  border-radius: 0.28vh;
  background-color: $main;
  width: 13.54vw;
  height: 11vw;
  box-shadow: 0.26vw 0.2vw 0.36vw rgba(0, 0, 0, 0.3);
  transition: transform 0.3s;

  &:hover {
    transform: scale(1.05);
    box-shadow: 0.4vw 0.4vw 0.36vw rgba(0, 0, 0, 0.3);
  }

  &-title {
    height: 2.29vw;
    text-align: center;
  }
}
</style>
