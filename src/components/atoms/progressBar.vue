<script>
export default {
  props: {
    class: String,
    score: {
      type: String,
      default: "",
    },
    descr: {
      type: String,
      default: "",
    },
    progress: {
      type: Number,
      required: true,
      default: 0,
    },
    color: {
      type: String,
      required: true,
    },
  },
};
</script>

<template>
  <div class="progress" :class="class" :style="`--i:${progress};--clr:${color};`">
    <div class="progress__category">
      <div class="progress__category-value">
        {{ score }}
        <span class="progress__category-descr">{{ descr }}</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.progress {
  position: relative;
  width: 6.25vw;
  height: 6.25vw;
  border-radius: 50%;
  background: $profile linear-gradient(to right, transparent 50%, var(--clr) 0);

  &::before {
    content: "";
    display: block;
    height: 100%;
    margin-left: 50%;
    transform-origin: left;
    border-radius: 0 100% 100% 0/50%;
    background: var(--clr);
    transform: rotate(calc(((var(--i) - 50) * 0.01turn)));
  }

  &::after {
    content: "";
    position: absolute;
    inset: 0.52vw;
    border-radius: 50%;
    background: $main;
  }

  &.contract {
    &::after {
      background-image: url("/src/assets/img/contract.png");
      background-size: 3.33vw;
      background-repeat: no-repeat;
      background-position: 1.3vw 0.78vw;
    }
  }

  &.test {
    &::after {
      background-image: url("/src/assets/img/test.png");
      background-size: 3.33vw;
      background-repeat: no-repeat;
      background-position: 1.2vw 0.76vw;
    }
  }

  &.less_50 {
    &::before {
      background: $profile;
      transform: rotate(calc(((var(--i) - 0) * 0.01turn)));
    }
  }

  &__category {
    &-value {
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: $f44;
      z-index: 1;
      font-weight: 600;
      line-height: 1.2;
    }

    &-descr {
      font-weight: 500;
    }
  }
}
</style>
