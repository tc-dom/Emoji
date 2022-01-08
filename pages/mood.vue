<template>
  <div>
   <v-card>
    <v-toolbar
      color="#2c3e50"
      flat
      dark
    >
      

      <v-toolbar-title>😘 Mood sound | nature sounds for your work</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs
          v-model="tab"
          dark
          color="#fff"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>

          <v-tab
            v-for="item in items"
            :key="item"
          >
            {{ item }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

   
        <v-card flat>
          <v-card-text v-text="text">
          </v-card-text>
         
        </v-card>
     
  </v-card>
  
  <NuxtChild/>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        tab: null,
        items: [
          'More', 'Smile face', 'videos', 'images', 'news',
        ],
        text: 'Copy the emoji you are interested in on this page and paste it into the clipboard in your editor.',
      }
    },
  }
</script>