<script>
export default {
  props: {
    darkTheme: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<template>
  <label class="switch">
    <input type="checkbox" />
    <span class="slider"></span>
  </label>

  <!-- <div class="themeSwitch">
    <label for="themeToggle" class="themeSwitch__label">
      <input
        type="checkbox"
        id="themeToggle"
        class="themeSwitch__toggle"
        :checked="darkTheme"
        @change="$emit('update:darkTheme', !darkTheme)"
      />
      <span class="themeSwitch__label-icon">
        <img
          v-if="darkTheme"
          src="img/moon.png"
          alt="Moon"
          class="themeSwitch__label-icon-moon"
        />
        <img v-else src="img/sun.png" alt="Sun" class="themeSwitch__label-icon-sun" />
      </span>
    </label>
  </div> -->
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

/* The switch - the box around the slider */
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

/* The slider */
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

input:checked + .slider {
  background-color: #2196f3;
}
input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}
input:checked + .slider:before {
  -webkit-transform: translateX(26px);
  -ms-transform: translateX(26px);
  transform: translateX(26px);
}

// .themeSwitch {
//   margin-left: auto;
//   &__toggle {
//     display: none;
//   }

//   &__label {
//     display: flex;
//     align-items: center;
//     cursor: pointer;
//     display: inline-block;

//     &-icon {
//       img {
//         width: calc((64px / 1920px) * 100vw);
//         height: calc((64px / 1920px) * 100vw);
//         transition: opacity 0.3s;
//       }

//       &-moon {
//         opacity: 0;
//       }

//       &-sun {
//         opacity: 1;
//       }
//     }
//   }
// }

// /* Стили для темной темы */
// .themeSwitch__toggle:checked + .themeSwitch__label .themeSwitch__label-icon-moon {
//   opacity: 1;
// }

// .themeSwitch__toggle:checked + .themeSwitch__label .themeSwitch__label-icon-sun {
//   opacity: 0;
// }
</style>
