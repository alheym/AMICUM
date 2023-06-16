<template>
  <div class="diagram progress" :class="class" :data-percent="percent">
    <div class="piece left"></div>
    <div class="piece right"></div>
  </div>
</template>

<script>
export default {
  props: {
    class: String,
    percent: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/styles/main";

.diagram {
  width: calc((120px / 1080px) * 100vh);
  height: calc((120px / 1080px) * 100vh);
  border-radius: 50%;
  background: $notification;
  position: relative;
  overflow: hidden;
}
.diagram::before {
  content: "";
  display: block;
  position: absolute;
  top: calc((10px / 1080px) * 100vh);
  left: calc((10px / 1080px) * 100vh);
  right: calc((10px / 1080px) * 100vh);
  bottom: calc((10px / 1080px) * 100vh);
  border-radius: 50%;
  background: $main;
  z-index: 3;
  opacity: 1;
}
.diagram .piece {
  width: 100%;
  height: 100%;
  left: 0;
  right: 0;
  overflow: hidden;
  position: absolute;
}
.diagram .piece::before {
  content: "";
  display: block;
  position: absolute;
  width: 50%;
  height: 100%;
}
.diagram .piece.left {
  transform: rotate(0deg);
  z-index: 2;
  border-radius: 50%; /* only FireFox < 75.0v (fix bug)*/
}
.diagram.over_50 .piece.left {
  transform: rotate(180deg);
}
.diagram .piece.right {
  transform: rotate(180deg);
  z-index: 1;
  border-radius: 50%; /* only FireFox < 75.0v (fix bug)*/
}
.diagram.over_50 .piece.right {
  transform: rotate(360deg);
}
.diagram .left::before {
  background: $profile;
}
.diagram.over_50 .left::before {
  background: $notification;
}
.diagram .right::before {
  background: $profile;
}
.diagram .text {
  position: absolute;
  z-index: 3;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
}
.diagram .text b {
  font-size: 32px;
}
.diagram .text span {
  font-size: 16px;
  display: block;
}
</style>
