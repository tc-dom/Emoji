<template>
  <v-app>
    <v-app-bar elevation="0" class="un-bg" fixed app height="80">
      <v-toolbar-title v-text="title" class="mr-5" />

      <v-btn text v-for="link in links" :key="link.title" :to="link.to">{{
        link.title
      }}</v-btn>

      <v-spacer />

      <v-btn icon @click="toggleTheme" color="orange">
        <v-icon
          >mdi-{{
            `${
              $vuetify.theme.dark
                ? "moon-waning-crescent"
                : "white-balance-sunny"
            }`
          }}</v-icon
        >
      </v-btn>
      <v-btn to="/abount" text class="mx-3">Abount</v-btn>
    </v-app-bar>
    <v-main>
      <div class="ma-3">
        <v-sheet outlined class="stamp_digit">
          <div class="side_timer">
            <div class="status_bar">
              <p>
                <v-chip small label>{{ title }}</v-chip>
                <v-chip small label
                  >{{ round }} | {{ loop }} : {{ Math.ceil(percent) }}%</v-chip
                >
              </p>

              <v-progress-linear rounded v-model="percent" height="5">
              </v-progress-linear>

              <div class="digit_timer">{{ minutes }}: {{ seconds }}</div>

              <v-btn @click="start()" color="#1abc9c" dark block class="pa-8 mt-5 mb-3" large>
                <v-icon v-if="s_titlel === 'L'">mdi-coffee</v-icon>
                <v-icon v-if="s_titlel === 'B'">mdi-numeric-5-circle</v-icon>
                <v-icon v-if="s_titlel === 'W'">mdi-briefcase</v-icon> |
                {{ btn }}</v-btn
              >
            </div>
            <div class="button_timer">
                <v-btn @click="nextStep(turn)" text color="#f39c12">
                      next step>>  </v-btn
                    >
              <v-dialog v-model="dialog" width="500">
                <template v-slot:activator="{ on, attrs }">
                  <v-btn color="red lighten-2" text v-bind="attrs" v-on="on">
                    reset
                  </v-btn>
                </template>

                <v-card>
                  <v-card-title class="text-h5 lighten-2">
                    Sure !
                  </v-card-title>

                  <v-card-text>
                    Are you sure you want to cancel all actions on this page?
                    <v-btn @click="reset()" text color="#f39c12">
                      reset now !</v-btn
                    >
                  </v-card-text>

                  <v-divider></v-divider>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="primary" text @click="dialog = false">
                      Cancel
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </div>
          </div>
          <v-sheet class="tc_dom un-bg" outlined>
            <Nuxt />
          </v-sheet>
        </v-sheet>
      </div>
      <GoToTop />
    </v-main>

    <v-footer absolute app>
      <span class="mx-auto">Emojy &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import GoToTop from "@/components/go-to-top";
var running = false,
  started = null;
export default {
  components: {
    GoToTop,
  },
  data() {
    ``;
    return {
      percent: 0,
      loading: 0,
      time: 1500,
      timebreak: "5 minutes",
      round: 1,
      turn:1,
      minutes: "25",
      seconds: "00",
      btn: "Start",
      title: "Work",
      s_titlel: "W",
      next: 2,
      loop: 1,
      dialog: false,
      links: [
        {
          title: "Home",
          to: "/",
        },
        {
          title: "Emoji",
          to: "/emoji",
        },
        {
          title: "Pan tone",
          to: "/pantone",
        },
        {
          title: "Mood sound",
          to: "/mood",
        },
      ],
      title: "Emojy",
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
    nextStep(x){
      console.log(x);
      console.log(this.loading);
      this.time = 1
      if(x ==1 ){
        this.loading = 1500
      }else if(x == 2){
        this.loading = 1800
      }else if(x == 3){
        this.loading = 3300
      }else if(x == 4){
        this.loading = 3600
      }else if(x == 5){
        this.loading = 5100
      }else if(x == 6){
        this.loading = 5400
      }else if(x == 7){
        this.loading = 6900
      }else{
        this.loading = 0
      }
      if(!running){
       this.start() 
      }
    },
    timeset() {
      this.loading += 1;
      this.percent = parseInt((this.loading / 7800) * 100, 10);
      
      this.time -= 1;
      this.minutes = parseInt(this.time / 60, 10);
      this.seconds = parseInt(this.time % 60, 10);
      if (this.time <= 0) {
        if(this.turn == 7){
          this.loading = 0
        }
        this.turn +=1
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
    toggleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
      localStorage.setItem("useDarkTheme", this.$vuetify.theme.dark.toString());
    },
  },
  mounted() {
    const theme = localStorage.getItem("useDarkTheme");
    if (theme) {
      if (theme == "true") {
        this.$vuetify.theme.dark = true;
      } else this.$vuetify.theme.dark = false;
    }
  },
};
</script>
