<template>
  <div>
    <v-card>
      <v-toolbar flat class="un-bg">
  <v-tabs v-model="tab" align-with-title>
            <v-tabs-slider color="yellow"></v-tabs-slider>

            <v-tab v-for="item in items" :key="item.title" :to="item.to">
              {{ item.title }}
            </v-tab>
          </v-tabs>
        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>

       
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
          to: "/emoji/1",
        },
        {
          title: "Occupations",
          to: "/emoji/2",
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
