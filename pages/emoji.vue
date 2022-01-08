<template>
  <div>
    <v-card>
      <v-toolbar color="#34495e" dark flat>
        <v-toolbar-title>😘 Emoji | Copy mode</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>

        <template v-slot:extension>
          <v-tabs v-model="tab" dark color="#fff" align-with-title>
            <v-tabs-slider color="yellow"></v-tabs-slider>

            <v-tab v-for="item in items" :key="item.title" :to="item.to">
              {{ item.title }}
            </v-tab>
          </v-tabs>
        </template>
      </v-toolbar>

      <v-card flat>
        <v-card-text v-text="text"> </v-card-text>
      </v-card>
    </v-card>

    <NuxtChild />
  </div>
</template>

<script>
export default {
  data() {
    return {
      tab: null,
      items: [
        {
          title: "More",
          to: "/emoji",
        },
        {
          title: "Emotions face",
          to: "/emoji/emotions",
        },
        {
          title: "Occupations",
          to: "/emoji/occupations",
        },
        {
          title: "Mood sound",
          to: "/mood",
        },
      ],
      text: "Copy the emoji you are interested in on this page and paste it into the clipboard in your editor.",
    };
  },
};
</script>
