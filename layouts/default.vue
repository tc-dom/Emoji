<template>
  <v-app>
    <v-app-bar dark fixed app height="80">
      <v-toolbar-title v-text="title"  class="mr-5"/>

      <v-btn text v-for="link in links" :key="link.title" :to="link.to">{{link.title}}</v-btn>
   

      <v-spacer />
      <v-btn>Donate</v-btn>

      <v-btn>Abount</v-btn>
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
    </v-app-bar>
    <v-main>
      <div class="ma-3"> 
        <v-sheet class="tc_dom" outlined>
        <Nuxt />
      </v-sheet>
      </div>
      <GoToTop/>
    </v-main>

    <v-footer absolute app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import GoToTop from "@/components/go-to-top";
export default {
  components:{
    GoToTop
  },
  data() {
    return {
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
         {
          title: "Timer",
          to: "/timer",
        },
      ],
      title: "Emojy",
    };
  },
   methods: {
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

<style>
.tc_dom{
  max-width: 1200px;
  width: 100%;
  margin: 10px auto;
  border-radius: 15px;
  overflow: hidden;
}

li {
  margin-bottom: 0.5rem;
}
li:first-letter {
  text-transform: uppercase;
}
.loading {
  display: inline-block;
  min-width: 1.5rem;
  height: 1.5rem;
  border: 4px solid rgba(9, 133, 81, 0.705);
  border-radius: 50%;
  border-top-color: #158876;
  animation: spin 1s ease-in-out infinite;
}
.list {
  width: 100%;
}
.emoji {
  font-size: 60px;
  border-radius: 10px;
  display: inline-block;
  margin: 5px;
  text-align: center;
  min-width: 80px;
}

.name-header {
  text-align: left;
  background: rgba(0, 0, 0, 0.2);
  padding: 2px 0 0 12px;
  position: -webkit-sticky;
  position: sticky;
  top: -1px;
}
.emojo {
  min-width: 122px;
}
@keyframes spin {
  to {
    -webkit-transform: rotate(360deg);
  }
}
</style>
