<template>
    <v-btn tile fab class="iron-man" @click="scrollTop" color="#f39c12" v-show="visible">
       <v-icon x-large color="white">
        mdi-chevron-up
      </v-icon>
    </v-btn>

</template>

<script>
export default {
  data() {
    return {
      visible: false,
    };
  },
  methods: {
    scrollTop: function () {
      this.intervalId = setInterval(() => {
        if (window.pageYOffset === 0) {
          clearInterval(this.intervalId);
        }
        window.scroll(0, window.pageYOffset - 100);
      }, 20);
    },
    scrollListener: function (e) {
      this.visible = window.scrollY > 100;
    },
  },
  mounted: function () {
    window.addEventListener("scroll", this.scrollListener);
  },
  beforeDestroy: function () {
    window.removeEventListener("scroll", this.scrollListener);
  },
};
</script>
<style>
.iron-man{
  position: fixed;
  bottom: 40px;
  right: 20px;
}
</style>
