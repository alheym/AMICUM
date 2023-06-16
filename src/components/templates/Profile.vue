<script>
import ProgressBar from "../molecules/progressBar.vue";

export default {
  components: {
    ProgressBar,
  },
  data() {
    return {
      percent: 14,
    };
  },

  mounted() {
    this.progressView();
  },
  watch: {
    precent() {
      this.progressView();
    },
  },
  methods: {
    progressView() {
      const diagramBoxes = this.$el.querySelectorAll(".diagram.progress");
      console.log(diagramBoxes);
      diagramBoxes.forEach((box) => {
        const deg = (360 * box.dataset.percent) / 100 + 180;
        if (box.dataset.percent >= 50) {
          box.classList.add("over_50");
        } else {
          box.classList.remove("over_50");
        }
        box.querySelector(".piece.right").style.transform = `rotate(${deg}deg)`;
      });
    },
  },
};
</script>

<template>
  <section class="profile">
    <div class="profile__menu">
      <div class="profile__menu-data">XX.XX.XXXX</div>
      <div class="profile__menu-out">Выход</div>
      <div class="profile__menu-theme"></div>
    </div>
    <div class="profile__info">
      <div class="profile__info-name">Фамилия Имя Отчество</div>
      <div class="profile__info-year">ХХ.ХХ.ХХХХ</div>
      <div class="profile__info-descr">Таб №: ГОКИ 0000</div>
      <div class="profile__info-position">Проходчик IV разряда</div>
    </div>

    <div class="profile__progress">
      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Инструктаж</div>

        <ProgressBar class="diagram progress over_50" :percent="100" />

        <!-- <div class="diagram progress over_50" data-percent="10">
          <div class="piece left"></div>
          <div
            class="piece right"
            style="transform: rotate(calc(180deg + 100deg * 360 / 100))"
          ></div>
          <div class="text">
            <div>
              <img src="" alt="" />
              <b>3</b>
              <span>дня</span>
            </div>
          </div>
        </div> -->
      </div>
      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Инструктаж</div>

        <ProgressBar class="diagram progress over_50" :percent="100" />
      </div>
      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Инструктаж</div>
        <ProgressBar class="diagram progress" :percent="12" />
      </div>
      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Инструктаж</div>
        <ProgressBar class="diagram progress over_50" :percent="100" />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.profile {
  max-width: calc((660px / 1920px) * 100vw);
  display: flex;
  padding: $grid_margin;
  flex-direction: column;
  background-color: $profile;
  border-top-right-radius: 20px;
  border-bottom-right-radius: 20px;
  box-shadow: 5px 2px 7px rgba(0, 0, 0, 0.3);

  &__menu {
    display: flex;
    height: calc((240px / 1080px) * 100vh);
    justify-content: space-between;

    &-out {
    }
  }

  &__info {
    padding: $grid_gutter $grid_gutter * 3;
    background-color: $main;
    border-radius: 3px;
    box-shadow: 1px 4px 3px rgba(0, 0, 0, 0.2);

    &-name {
      font-weight: 600;
      font-size: calc((32px / 1920px) * 100vw);
      margin-bottom: calc((5px / 1080px) * 100vh);
    }

    &-year {
      font-size: calc((24px / 1920px) * 100vw);
      margin-bottom: calc((10px / 1080px) * 100vh);
    }

    &-descr {
      font-size: calc((16px / 1920px) * 100vw);
      margin-bottom: calc((10px / 1080px) * 100vh);
    }

    &-position {
      font-size: calc((16px / 1920px) * 100vw);
      margin-bottom: calc((5px / 1080px) * 100vh);
    }
  }

  &__progress {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: calc((20px / 1080px) * 100vh);
    margin-top: calc((20px / 1920px) * 100vw);

    &-item {
      padding-left: calc((60px / 1080px) * 100vh);
      padding-right: calc((60px / 1080px) * 100vh);

      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;
      border-radius: 3px;
      background-color: $main;
      width: calc((280px / 1920px) * 100vw);
      height: calc((260px / 1080px) * 100vh);

      &-title {
        font-size: calc((16px / 1920px) * 100vw);
      }
    }
  }
}
</style>
