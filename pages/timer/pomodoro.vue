<template>
  
</template>
<script>
var running = false,
  started = null;
export default {
  data() {
    return {
      percent: 0,
      loading: 0,
      time: 1500,
      timebreak: "5 minutes",
      round: 1,
      minutes: "25",
      seconds: "00",
      btn: "Start",
      title: "Work",
      s_titlel: "W",
      next: 2,
      loop: 1,
      dialog: false,
    };
  },
  head() {
    return {
      title: this.s_titlel + " | " + this.minutes + " : " + this.seconds,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content: "My custom description",
        },
      ],
    };
  },
  methods: {
    start() {
      if (running) {
        running = false;
        this.btn = "Resume";
        clearInterval(started);
      } else {
        started = setInterval(this.timeset, 1000);
        this.btn = "Pause";
        running = true;
      }
    },

    timeset() {
      this.loading += 1;
      this.percent = parseInt((this.loading / 7800) * 100, 10);
      this.time -= 1;
      this.minutes = parseInt(this.time / 60, 10);
      this.seconds = parseInt(this.time % 60, 10);
      if (this.time <= 0) {
        if (this.round <= 3) {
          if (this.next == 1) {
            this.time = 1500;
            this.title = "Work";
            this.s_titlel = "W";
            this.timebreak = "5 minutes";
            this.next = 2;
            this.round += 1;
          } else {
            this.time = 300;
            this.title = "Break";
            this.s_titlel = "B";
            this.next = 1;
          }
        } else {
          this.time = 900;
          this.round = 0;
          this.title = "long break";
          this.s_titlel = "L";
          this.timebreak = "15 minutes";
          this.loop += 1;
          this.next = 1;
          this.loading = 0;
        }
      }
    },
    reset() {
      running = false;
      this.dialog = false;
      clearInterval(started);
      started = null;
      this.percent = 0;
      this.loading = 0;
      this.time = 1500;
      this.timebreak = "5 minutes";
      this.round = 1;
      this.minutes = "25";
      this.seconds = "00";
      this.btn = "Start";
      this.title = "Work";
      this.s_titlel = "W";
      this.next = 2;
      this.loop = 1;
    },
  },
};
</script>
