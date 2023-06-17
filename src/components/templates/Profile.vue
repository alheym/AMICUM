<script>
import ProgressBar from "../molecules/progressBar.vue";
import ThemeSwitch from "../atoms/toggleSwitch.vue";

export default {
  components: {
    ProgressBar,
    ThemeSwitch,
  },
  data() {
    return {
      darkTheme: false, // Изначальное значение темы (false - светлая, true - темная)
    };
  },
  props: {
    fullName: {
      type: String,
      default: "Фамилия Имя Отчество",
    },
    birthday: {
      type: String,
      default: "ХХ.ХХ.ХХХХ",
    },
    descr: {
      type: String,
      default: "Таб №: ГОКИ 0000",
    },
    position: {
      type: String,
      default: "Проходчик IV разряда",
    },
  },
  methods: {
    handleLogout() {
      console.log("Выход");
    },
  },
};
</script>

<template>
  <section class="profile">
    <div class="profile__menu">
      <div class="profile__menu-date">
        <div class="profile__menu-date-year">XX.XX.XXXX</div>
        <div class="profile__menu-date-time">XX:XX</div>
      </div>
      <div class="profile__menu-out" @click="handleLogout">
        Выход
        <img src="img/out.png" alt="Выход" class="profile__menu-out-icon" />
      </div>
    </div>

    <ThemeSwitch :dark-theme="darkTheme" />
    <div class="profile__theme">toggle</div>

    <div class="profile__info">
      <div class="profile__info-fullName">{{ fullName }}</div>
      <div class="profile__info-birthday">{{ birthday }}</div>
      <div class="profile__info-descr">{{ descr }}</div>
      <div class="profile__info-position">{{ position }}</div>
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
  width: 34.375%;
  display: flex;
  padding: calc((30px / 1920px) * 100vw);
  flex-direction: column;
  background-color: $profile;
  border-top-right-radius: calc((20px / 1080px) * 100vh);
  border-bottom-right-radius: calc((20px / 1080px) * 100vh);
  box-shadow: 5px 2px 7px rgba(0, 0, 0, 0.3);

  &__menu {
    display: flex;
    // height: 22.22%;
    margin-bottom: 11%;
    justify-content: space-between;
    &-date {
      display: flex;
      flex-direction: column;
      &-year,
      &-time {
        font-size: calc((16px / 1920px) * 100vw);
        font-weight: 500;
      }
    }

    &-out {
      cursor: pointer;
      display: flex;
      align-items: center;
      font-size: calc((16px / 1920px) * 100vw);
      font-weight: 500;
      &-icon {
        margin-left: calc((15px / 1920px) * 100vw);
        width: calc((40px / 1920px) * 100vw);
      }
    }
  }

  &__theme {
    margin-left: auto;
  }

  &__info {
    padding: calc((30px / 1920px) * 100vw);
    background-color: $main;
    border-radius: calc((3px / 1080px) * 100vh);
    box-shadow: 5px 4px 7px rgba(0, 0, 0, 0.2);

    &-fullName {
      font-weight: 600;
      font-size: calc((32px / 1920px) * 100vw);
      margin-bottom: calc((5px / 1080px) * 100vh);
    }

    &-birthday {
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

      @media screen and (max-width: 700px) {
        width: auto;
        height: calc((170px / 1080px) * 100vh);
      }
    }

    @media screen and (max-width: 700px) {
      grid-template-columns: 1fr;
    }
  }
}
</style>
