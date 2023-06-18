<script>
import ActionItem from "../molecules/actionItem.vue";

export default {
  components: {
    ActionItem,
  },
  data() {
    return {
      items: [
        {
          id: 1,
          image: "img/work.png",
          title: "Начать работу",
        },
        {
          id: 2,
          image: "img/message.png",
          title: "Уведомления",
          notificationCount: 3,
        },
        {
          id: 3,
          image: "img/education.png",
          title: "Обучение",
        },
        {
          id: 4,
          image: "img/achievements.png",
          title: "Достижения",
        },
      ],
    };
  },
  methods: {
    handleItemClick(title) {
      console.log("Кликнут элемент:", title);
    },
  },
};
</script>

<template>
  <section class="workspace">
    <div class="workspace__logo"></div>
    <div class="workspace__actions">
      <ActionItem
        v-for="item in items"
        :key="item.id"
        :image="item.image"
        :title="item.title"
        :notificationCount="item.notificationCount"
        @item-clicked="handleItemClick"
      />
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.workspace {
  padding: 0.52vw 0.78vw;
  width: 100%;
  display: flex;
  flex-direction: column;

  &__logo {
    margin-left: auto;
    width: 11.25vw;
    height: 3.96vw;
    background-image: url("/src/assets/img/logo.png");
    background-size: 11.25vw 3.96vw;
    background-repeat: no-repeat;
  }

  &__actions {
    align-self: center;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: 5.2vw;
    margin: 5.99vw 9.11vw 0;
  }
}
</style>
