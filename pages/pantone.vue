<template>
  <div>
   <v-card>
    <v-toolbar
      color="#222"
      dark
      flat
    >
      

      <v-toolbar-title>😘 Pantone | Copy mode</v-toolbar-title>

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
          
          color="#fff"
          align-with-title
        >
          <v-tabs-slider color="yellow"></v-tabs-slider>

          <v-tab
            v-for="item in items"
            :key="item.title"
            :to="item.to"
          >
            {{ item.title }}
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
          {
          title: "More",
          to: "/pantone",
        },
        {
          title: "popular code",
          to: "/pantone/app",
        },
        {
          title: "generator",
          to: "/pantone/generator",
        },
        {
          title: "Quick",
          to: "/pantone/quick",
        },
        ],
        text: 'Copy the emoji you are interested in on this page and paste it into the clipboard in your editor.',
      }
    },
  }
</script>