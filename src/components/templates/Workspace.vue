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
  padding: calc((10px / 1920px) * 100vw) calc((15px / 1920px) * 100vw);
  width: 100%;
  display: flex;
  flex-direction: column;

  &__logo {
    margin-left: auto;
    // margin-bottom: calc((10px / 1920px) * 100vw);
    width: calc((216px / 1920px) * 100vw);
    height: calc((76px / 1920px) * 100vw);
    // background-color: yellow;
    background-image: url("/src/assets/img/logo.png");
    background-size: calc((216px / 1920px) * 100vw) calc((76px / 1920px) * 100vw);
    background-repeat: no-repeat;
  }

  &__actions {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-gap: calc((100px / 1920px) * 100vw);
    margin: calc((155px / 1920px) * 100vw) calc((175px / 1920px) * 100vw) 0;
  }
}
</style>
