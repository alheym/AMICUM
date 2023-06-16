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

<script>
export default {
  props: {
    class: String,
    value: {
      type: String,
      default: "",
    },
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
      default: 0,
    },
    color: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.progress {
  position: relative;
  width: calc((120px / 1920px) * 100vw);
  height:  calc((120px / 1920px) * 100vw);
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
    inset: calc((10px / 1920px) * 100vw);
    border-radius: 50%;
    background: $main;
  }

  &.contract {
    &::after {
      background-image: url("/src/assets/img/contract.png");
      background-size: calc((64px / 1920px) * 100vw);
      background-repeat: no-repeat;
      background-position: 70% 50%;
    }
  }

  &.test {
    &::after {
      background-image: url("/src/assets/img/test.png");
      background-size: calc((64px / 1920px) * 100vw);
      background-repeat: no-repeat;
      background-position: 65% 50%;
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
      font-size: calc((44px / 1920px) * 100vw);
      z-index: 1;
      font-weight: 600;
      line-height: 1.2;
    }

    &-descr {
      font-size: calc((16px / 1920px) * 100vw);
      font-weight: 500;
    }
  }
}

</style>
