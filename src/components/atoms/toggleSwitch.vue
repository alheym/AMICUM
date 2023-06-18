<script>
export default {
  data() {
    return {
      isChecked: false,
    };
  },
  methods: {
    toggleSwitch() {
      if (this.isChecked) {
        console.log("moon");
      } else console.log("sun");
    },
  },
};
</script>

<template>
  <div class="themeSwitch">
    <label class="themeSwitch__switch">
      <input type="checkbox" v-model="isChecked" @change="toggleSwitch" />
      <span class="themeSwitch__switch-slider"></span>
    </label>
  </div>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.themeSwitch {
  &__switch {
    position: relative;
    display: inline-block;
    width: calc((65px / 1920px) * 100vw);
    height: calc((20px / 1920px) * 100vw);

    input {
      display: none;
    }

    &-slider {
      position: absolute;
      cursor: pointer;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: $main;
      -webkit-transition: 0.4s;
      transition: 0.4s;
      border-radius: calc((34px / 1920px) * 100vw);

      &::before {
        position: absolute;
        content: "";
        height: calc((64px / 1920px) * 100vw);
        width: calc((64px / 1920px) * 100vw);
        left: calc((-22px / 1920px) * 100vw);
        bottom: calc((-22px / 1920px) * 100vw);
        background-image: url("/src/assets/img/sun.png");
        background-size: calc((64px / 1920px) * 100vw);
        background-repeat: no-repeat;
        -webkit-transition: 0.4s;
        transition: 0.4s;
        border-radius: 50%;
      }
    }
  }
}

input:checked + .themeSwitch__switch-slider {
  background-color: #5f6674;
}

input:checked + .themeSwitch__switch-slider:before {
  -webkit-transform: translateX(calc((40px / 1920px) * 100vw));
  -ms-transform: translateX(calc((40px / 1920px) * 100vw));
  transform: translateX(calc((40px / 1920px) * 100vw));
  left: calc((-13px / 1920px) * 100vw);
  bottom: calc((-18px / 1920px) * 100vw);
  background-image: url("/src/assets/img/moon.png");
  background-size: calc((64px / 1920px) * 100vw);
  background-repeat: no-repeat;
  background-position: 50% 50%;
}
</style>
