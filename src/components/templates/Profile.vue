<script>
import ProgressBar from "../molecules/progressBar.vue";
import testImage from "@/assets/img/test.png";

export default {
  components: {
    ProgressBar,
  },
};
</script>

<template>
  <section class="profile">
    <div class="profile__menu">
      <div class="profile__menu-data">XX.XX.XXXX</div>
      <div class="profile__menu-out">Выход</div>
      <div class="profile__menu-theme">toggle</div>
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
        <ProgressBar class="contract" progress="100" color="#add919" />
      </div>
      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Предсменный экзаменатор</div>

        <ProgressBar class="test" progress="100" color="#add919" />
      </div>

      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Тестов выполнено</div>
        <ProgressBar class="less_50" progress="25" score="12" color="#add919" />
      </div>

      <div class="profile__progress-item">
        <div class="profile__progress-item-title">Аттестация через</div>
        <ProgressBar
          class="less_50 with_descr"
          progress="15"
          score="3"
          descr="дня"
          color="#ef7f1b"
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.profile {
  width: calc((660px / 1920px) * 100vw);
  display: flex;
  padding: calc((30px / 1920px) * 100vw);
  flex-direction: column;
  background-color: $profile;
  border-top-right-radius: calc((20px / 1080px) * 100vh);
  border-bottom-right-radius: calc((20px / 1080px) * 100vh);
  box-shadow: 5px 2px 7px rgba(0, 0, 0, 0.3);

  &__menu {
    display: flex;
    height: 22.22%;
    justify-content: space-between;

    &-out {
    }
  }

  &__info {
    padding: calc((30px / 1920px) * 100vw);
    background-color: $main;
    border-radius: calc((3px / 1080px) * 100vh);
    box-shadow: 5px 4px 7px rgba(0, 0, 0, 0.2);

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
    grid-gap: calc((20px / 1920px) * 100vw);
    margin-top: calc((20px / 1080px) * 100vh);

    &-item {
      padding: 0 calc((60px / 1920px) * 100vw) calc((20px / 1920px) * 100vw);
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;
      border-radius: calc((3px / 1080px) * 100vh);
      background-color: $main;
      width: calc((280px / 1920px) * 100vw);
      height: calc((260px / 1080px) * 100vh);
      box-shadow: 5px 4px 7px rgba(0, 0, 0, 0.2);

      &-title {
        height: calc((44px / 1080px) * 100vh);
        text-align: center;
        font-size: calc((16px / 1920px) * 100vw);
      }
    }
  }
}
</style>
