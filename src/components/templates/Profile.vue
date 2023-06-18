<script>
import ProgressBar from "../atoms/progressBar.vue";
import ThemeSwitch from "../atoms/toggleSwitch.vue";
import ProfileItem from "../molecules/profileItem.vue";

export default {
  components: {
    ProgressBar,
    ThemeSwitch,
    ProfileItem,
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
  data() {
    return {
      currentTime: "",
    };
  },
  methods: {
    handleLogout() {
      console.log("Выход");
    },

    handleItemClick(title) {
      console.log("Click:", title);
    },

    getCurrentDateTime() {
      const currentDate = new Date();
      const date = currentDate.toLocaleDateString("ru-RU", {
        day: "2-digit",
        month: "2-digit",
        year: "numeric",
      });
      const time = currentDate.toLocaleTimeString("ru-RU", {
        hour: "2-digit",
        minute: "2-digit",
      });
      return { date, time };
    },
  },
  computed: {
    currentDateTime() {
      return this.getCurrentDateTime();
    },
  },
  mounted() {
    this.currentTime = this.getCurrentDateTime().time;
    setInterval(() => {
      this.currentTime = this.getCurrentDateTime().time;
    }, 1000);
  },
};
</script>

<template>
  <section class="profile">
    <div class="profile__header">
      <div class="profile__menu">
        <div class="profile__menu-date">
          <div class="profile__menu-date-year">{{ currentDateTime.date }}</div>
          <div class="profile__menu-date-time">{{ currentTime }}</div>
        </div>
        <div class="profile__menu-out" @click="handleLogout">
          Выход
          <img src="img/out.png" alt="Выход" class="profile__menu-out-icon" />
        </div>
      </div>

      <div class="profile__theme">
        <ThemeSwitch />
      </div>
    </div>

    <div class="profile__info">
      <div class="profile__info-fullName">{{ fullName }}</div>
      <div class="profile__info-birthday">{{ birthday }}</div>
      <div class="profile__info-descr">{{ descr }}</div>
      <div class="profile__info-position">{{ position }}</div>
    </div>

    <div class="profile__progress">
      <ProfileItem
        title="Инструктаж"
        class="contract"
        :progress="100"
        color="#add919"
        @item-clicked="handleItemClick"
      />
      <ProfileItem
        title="Предсменный экзаменатор"
        class="test"
        :progress="100"
        color="#add919"
        @item-clicked="handleItemClick"
      />
      <ProfileItem
        title="Тестов выполнено"
        class="less_50"
        :progress="25"
        score="12"
        color="#add919"
        @item-clicked="handleItemClick"
      />
      <ProfileItem
        title="Аттестация через"
        class="less_50 with_descr"
        :progress="15"
        score="3"
        descr="дня"
        color="#ef7f1b"
        @item-clicked="handleItemClick"
      />
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.profile {
  width: 34.375vw;
  display: flex;
  padding: 2.08vw;
  flex-direction: column;
  background-color: $profile;
  border-top-right-radius: 1.85vh;
  border-bottom-right-radius: 1.85vh;
  box-shadow: 0.26vw 0.2vw 0.36vw rgba(0, 0, 0, 0.3);

  &__menu {
    display: flex;
    justify-content: space-between;

    &-date {
      display: flex;
      flex-direction: column;
      
      &-year,
      &-time {
        font-weight: 500;
      }
    }

    &-out {
      cursor: pointer;
      display: flex;
      align-items: center;
      font-weight: 500;

      &-icon {
        width: 2.08vw;
        height: 2.08vw;
        background-image: url("/src/assets/img/out.png");
        background-size: 2.08vw;
        background-repeat: no-repeat;
        margin-left: 0.78vw;
      }
    }
  }

  &__header {
    display: flex;
    flex-direction: column;
    height: 7.81vw;
    justify-content: space-between;
    margin-bottom: 3.65vw;
  }

  &__theme {
    margin-left: auto;
  }

  &__info {
    padding: 1.04vw 1.56vw;
    background-color: $main;
    border-radius: 0.28vh;
    box-shadow: 0.26vw 0.2vw 0.36vw rgba(0, 0, 0, 0.3);

    &-fullName {
      font-weight: 600;
      font-size: $f32;
      margin-bottom: 0.26vw;
    }

    &-birthday {
      font-size: $f24;
      margin-bottom: 0.52vw;
    }

    &-descr {
      margin-bottom: 0.52vw;
    }
  }

  &__progress {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 1.04vw;
    margin-top: 1.04vw;
  }
}
</style>
