<template>
  <div>
    <h2>Carousel project</h2>
    <!-- <carousel-transition-end :imgList="imgList"></carousel-transition-end> -->
    <carousel-else-if :imgList="imgList"></carousel-else-if>
  </div>
</template>

<script>
import carouselTransitionEnd from "./components/carouselTransitionEnd";
import carouselElseIf from "./components/carouselElseIf";
export default {
  data: function() {
    return {
      imgList: [
        require("./assets/red.png"),
        require("./assets/orange.png"),
        require("./assets/yellow.png"),
        require("./assets/blue.png"),
        require("./assets/purple.png")
      ]
    };
  },
  components: {
    carouselTransitionEnd,
    carouselElseIf
  }
};
</script>

<style lang="scss" scoped>
</style>