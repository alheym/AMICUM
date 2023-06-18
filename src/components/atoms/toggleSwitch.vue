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
        console.log("theme: moon");
      } else console.log("theme: sun");
    },
  },
};
</script>

<template>
  <div class="themeSwitch">
    <label class="themeSwitch__switch">
      <input type="checkbox" name="switch" v-model="isChecked" @change="toggleSwitch" />
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
    width: 3.38vw;
    height: 1.04vw;

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
      transition: 0.4s;
      border-radius: 1.77vw;

      &::before {
        position: absolute;
        content: "";
        height: 3.33vw;
        width: 3.33vw;
        left: -1.14vw;
        bottom: -1.14vw;
        transition: 0.4s;
        border-radius: 50%;
        background-image: url("/src/assets/img/sun.png");
        background-size: 3.33vw;
        background-repeat: no-repeat;
      }
    }
  }
}

input:checked + .themeSwitch__switch-slider {
  background-color: #5f6674;
}

input:checked + .themeSwitch__switch-slider:before {
  transform: translateX(2.08vw);
  left: -0.68vw;
  bottom: -0.94vw;
  background-image: url("/src/assets/img/moon.png");
  background-size: 3.33vw;
  background-repeat: no-repeat;
  background-position: 50% 50%;
}
</style>
