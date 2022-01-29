<template>
  <div>
    <v-sheet max-width="1000" class="ma-2 mx-auto">
      <v-btn outlined color="#888"> School day at your room </v-btn>
      <v-btn> Make Night </v-btn>
      <v-btn> Beach holiday </v-btn>
      <v-btn> Nature </v-btn>
      <v-btn> Rainy day </v-btn>
      <v-row dense>
        <v-col v-for="(mood, index) in moods" :key="mood.title">
          <audio :id="index">
            <source
              :src="'/sound/mood/' + mood.title + '.mp3'"
              type="audio/ogg"
            />
            <source
              :src="'/sound/mood/' + mood.title + '.mp3'"
              type="audio/mpeg"
            />
          </audio>
          <div class="box_sound">
            <span @click="playAudio(index)" class="hover_btn">
              <v-sheet outlined class="icon_sound">
                <p class="title_box">{{ mood.title }}</p>
                <v-icon large class="mood-btn">{{ mood.icon }}</v-icon>
              </v-sheet>
            </span>
            <v-sheet class="volume_sound mx-auto" max-width="200px">
              <v-progress-linear
                :active="mood.play"
                :indeterminate="mood.play"
                rounded
                color="yellow darken-2"
              ></v-progress-linear>

              <v-slider
                v-show="mood.play"
                @change="onChange(mood.value, index)"
                v-model="mood.value"
                step="5"
                thumb-label
                ticks
              ></v-slider>
            </v-sheet>
          </div>
        </v-col>
      </v-row>
    </v-sheet>
  </div>
</template>

<script>

export default {
  data() {
    return {
      school:[3],
      moods: [
        { icon: "mdi-weather-pouring", title: "Rain", play: false, value: 50 },
        {
          icon: "mdi-weather-night-partly-cloudy",
          title: "Night",
          play: false,
          value: 70,
        },
        { icon: "mdi-train", title: "Train", play: false, value: 70 },
        { icon: "mdi-waves", title: "Sea", play: false, value: 70 },
        { icon: "mdi-sail-boat", title: "Ship", play: false, value: 70 },
        { icon: "mdi-airplane", title: "Plane", play: false, value: 70 },
        { icon: "mdi-highway", title: "Traffic", play: false, value: 70 },
        {
          icon: "mdi-weather-lightning",
          title: "Thunder",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-city-variant-outline",
          title: "Stations",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-keyboard-variant",
          title: "Keyboard",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-draw",
          title: "Writing",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-book-open-page-variant-outline",
          title: "Library",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-weather-windy-variant",
          title: "Windy",
          play: false,
          value: 70,
        },
        {
          icon: "mdi-window-closed-variant",
          title: "Window",
          play: false,
          value: 70,
        },
        { icon: "mdi-weather-night", title: "Cricket", play: false, value: 70 },
        { icon: "mdi-bird", title: "Bird", play: false, value: 70 },
        { icon: "mdi-paw", title: "Wolf", play: false, value: 70 },
        { icon: "mdi-walk", title: "Walk", play: false, value: 70 },
        { icon: "mdi-bugle", title: "Horn", play: false, value: 70 },
        { icon: "mdi-alarm", title: "Clock", play: false, value: 70 },
        { icon: "mdi-fan", title: "Fan", play: false, value: 70 },
        { icon: "mdi-fire", title: "Fire", play: false, value: 70 },
        { icon: "mdi-school-outline", title: "School", play: false, value: 70 },
        {
          icon: "mdi-shaker-outline",
          title: "Cooking",
          play: false,
          value: 70,
        },
        { icon: "mdi-water-outline", title: "Drop", play: false, value: 70 },
        { icon: "mdi-wave", title: "Wave", play: false, value: 70 },
      ],

      x: false,
    };
  },
  created() {},
  methods: {
    onChange(value, index) {
      var x = document.getElementById(index);
      x.volume = this.moods[index].value / 100;
    },
    playAudio(id) {
  
      var x = document.getElementById(id);
      if (x.loop) {
        x.loop = false;
        this.moods[id].play = false;
        x.pause();
      } else {
        this.moods[id].play = true;
        x.loop = true;
        x.volume = this.moods[id].value / 100;
        x.load();
        x.play();
      }
    },
  },
  mounted() {},
};
</script>
<style>
.box_sound {
  display: block;
  min-width: 220px;
  min-height: 220px;
}
.title_box{
  color: #888;
}
.volume_sound {
  display: block;
  border-radius: 5px;
  margin: 2px 10px;
  padding: 0px 10px;
}
.icon_sound {
  display: block;
  margin: 10px;
  background: darkgoldenrod;
  border-radius: 20px;
  min-height: 190px;
  cursor: pointer;
  padding: 10px;
}
.icon_sound:hover {
  transition: 0.3s;
  box-shadow: 0px 0px 8px #999;
}
.hover_btn {
  cursor: pointer;
}
.samble {
  z-index: 1;

  background: crimson !important;
  display: block;
}
.mood-box {
  border-radius: 25px !important;
}
.mood-btn {
  display: block !important;
  margin: auto !important;
  text-align: center;
  height: 100px;
}
i.mood-btn {
  font-size: 70px !important;
}
</style>
