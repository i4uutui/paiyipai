<template>
  <div></div>
  <!-- <div
    class="home"
    :style="top"
    style="position:fixed;"
    id="right-nav"
    @touchmove="touchmove($event)"
  >
    <div class="homeCon bg-color-red" :class="homeActive === true ? 'on' : ''">
      <router-link
        :to="'/'"
        class="iconfont icon-shouye-xianxing"
      ></router-link>
      <router-link
        :to="'/cart'"
        class="iconfont icon-caigou-xianxing"
      ></router-link>
      <router-link :to="'/user'" class="iconfont icon-yonghu1"></router-link>
    </div>
    <div class="pictrue" @click="open">
      <img
        :src="
          homeActive === true
            ? require('../assets/images/close.gif')
            : require('../assets/images/open.gif')
        "
        class="image"
      />
    </div>
  </div> -->
</template>
<script>
import { mapGetters } from "vuex";
export default {
  name: "Home",
  props: {},
  data: function() {
    return {
      top: ""
    };
  },
  computed: mapGetters(["homeActive"]),
  methods: {
    touchmove(event) {
      event.preventDefault();
      let top =
        event.touches[0].pageY -
        (document.documentElement.scrollTop || document.body.scrollTop) -
        this.$el.clientHeight;

      if (top > 390) top = 390;
      else if (top < 55) top = 55;
      this.top = "top:" + top + "px";
    },
    open: function() {
      this.homeActive
        ? this.$store.commit("CLOSE_HOME")
        : this.$store.commit("OPEN_HOME");
    }
  }
};
</script>
<style scoped></style>
