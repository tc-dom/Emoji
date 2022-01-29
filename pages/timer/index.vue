<template>
  <div class="stamp_digit">
    <div class="digit_timer">{{ time }}</div>
    <div class="button_timer">
      <v-btn @click="start()">Start</v-btn>
      <v-btn @click="stop()">Stop</v-btn>
      <v-btn @click="reset()">Reset</v-btn>
    </div>
  </div>
</template>
<script>
var timeBegan = null,
  timeStopped = null,
  stoppedDuration = 0,
  started = null,
  running = false;
export default {
  data() {
    return {
      time: "00:00:00.000",
    };
  },
  created() {
    console.log(running);
    window.addEventListener("keydown", (e) => {
      if (e.key === ' ' || e.key === 'Spacebar') {
        if (running) {
          this.stop();
        } else {
          this.start();
        }
      }
    });
  },
  methods: {
    start() {
      if (running) return;

      if (timeBegan === null) {
        this.reset();
        timeBegan = new Date();
      }

      if (timeStopped !== null) {
        stoppedDuration += new Date() - timeStopped;
      }

      started = setInterval(this.clockRunning, 10);
      running = true;
    },

    stop() {
      running = false;
      timeStopped = new Date();
      clearInterval(started);
    },
    reset() {
      running = false;
      clearInterval(started);
      stoppedDuration = 0;
      timeBegan = null;
      timeStopped = null;
      this.time = "00:00:00.000";
    },
    clockRunning() {
      var currentTime = new Date(),
        timeElapsed = new Date(currentTime - timeBegan - stoppedDuration),
        hour = timeElapsed.getUTCHours(),
        min = timeElapsed.getUTCMinutes(),
        sec = timeElapsed.getUTCSeconds(),
        ms = timeElapsed.getUTCMilliseconds();

      this.time =
        this.zeroPrefix(hour, 2) +
        ":" +
        this.zeroPrefix(min, 2) +
        ":" +
        this.zeroPrefix(sec, 2) +
        "." +
        this.zeroPrefix(ms, 3);
    },

    zeroPrefix(num, digit) {
      var zero = "";
      for (var i = 0; i < digit; i++) {
        zero += "0";
      }
      return (zero + num).slice(-digit);
    },
  },
};
</script>

