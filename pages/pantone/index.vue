<template>
  <div>
    <div class="container">
      <input type="text" v-model="message" />
      <button
        type="button"
        v-clipboard:copy="message"
        v-clipboard:success="onCopy"
        v-clipboard:error="onError"
      >
        Copy!
      </button>
    </div>
    <v-row dense>
      <v-col class="inline" v-for="(color, i) in colors" :key="i">
        <v-card class="ma-3" min-width="200">
          <v-sheet height="180" :color="'#' + color.code"></v-sheet>
          <v-card-title> #{{ color.code }} </v-card-title>
          <v-card-subtitle> {{ color.title }} </v-card-subtitle>
          <v-card-actions>
            <v-btn color="orange lighten-2" text> Generator </v-btn>

            <v-spacer></v-spacer>

            <v-btn
              v-clipboard:copy="color.code"
              v-clipboard:success="onCopy"
              v-clipboard:error="onError"
              icon
         
            >
              <v-icon>mdi-card-multiple-outline</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>
<script>
import Vue from "vue";
import VueClipboard from "vue-clipboard2";
VueClipboard.config.autoSetContainer = true; // add this line
Vue.use(VueClipboard);
export default {
  data() {
    return {
      message: "Copy These Text",
      colors: [
        {
          code: "f39c12",
          title: "emojy orange",
        },
        {
          code: "ef5350",
          title: "emojy red",
        },
        {
          code: "fff346",
          title: "sofe yellow",
        },
        {
          code: "2bd598",
          title: "medium orange",
        },
        {
          code: "192f3e",
          title: "medium orange",
        },
        {
          code: "7852a9",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
        {
          code: "f39c12",
          title: "medium orange",
        },
      ],
    };
  },
  methods: {
    onCopy: function (e) {
      alert("You just copied: " + e.text);
    },
    onError: function (e) {
      alert("Failed to copy texts");
    },
  },
};
</script>
<style>
.inline {
  display: inline-block;
}
</style>
