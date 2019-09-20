<template>
  <div id="flowblock">
    <ul
      id="img"
      ref="child"
      :class="{ 'no-transition': noTrans }"
      :style="{
        height: '300px',
        transform: `translate(${-300 * index}px, 0)`
      }"
      @transitionend="handle_last"
    >
      <li v-for="(item, index) in imgList" :key="index">
        <img :src="item" />
      </li>
      <li>
        <img :src="imgList[0]" />
      </li>
    </ul>
    <br />
    <button @click="slideHandler">click</button>
  </div>
</template>

<script>
export default {
  props: ["imgList"],
  data() {
    return {
      index: 0,
      noTrans: false
    };
  },
  methods: {
    slideHandler() {
      this.noTrans = false;
      if (this.index <= this.imgList.length - 1) {
        this.index++;
      }
      console.log(this.index, this.imgList.length);
    },
    handle_last() {
      console.log("transion");
      if (this.index == this.imgList.length) {
        this.noTrans = true;
        this.index = 0;
      }
    }
  },
  mounted() {
    window.setInterval(this.slideHandler, 1000);
  }
};
</script>

<style scoped>
#flowblock {
  width: 300px;
  height: 300px;
  /* position: relative; */
  overflow: hidden;
}
#img {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
  transition: transform 300ms ease-in-out;
  /* position: absolute; */
}
.no-transition {
  transition: none !important;
}
#img > li {
  display: inline-block;
  width: 300px;
  flex-shrink: 0;
}
</style>