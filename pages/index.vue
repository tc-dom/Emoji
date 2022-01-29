<template>
  <div>
    <v-sheet class="pa-5">This app for writer,bloger,or computer users for create time 
      <p>you can use this app about copy emoji from this page or play some sound on mood sound page s</p>
    </v-sheet>
    <v-sheet class="pa-5">
      <v-row>
        <v-col v-for="i in menu" :key="i.title" cols="12" lg="4" md="6" sm="4">
          <v-sheet rounded class="ma-3" outlined>
            <v-list-item :to="i.link">
              <v-list-item-icon>
                 <v-icon>{{i.icon}}</v-icon>
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title>{{i.title}}</v-list-item-title>
                <v-list-item-subtitle>{{i.subtitle}}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-sheet>
        </v-col>
      </v-row>
    </v-sheet>
  </div>
</template>

<script>
export default {
  data(){
    return{
      menu:[{
        title:"Emoji",subtitle:"Copy emoji to press in your work or project"
        ,link:"/emoji",icon:"mdi-emoticon-cool-outline"
      },
      {
        title:"Pantone",subtitle:"Copy emoji to press in your work or project"
        ,link:"/pantone",icon:"mdi-palette"
      },
      {
        title:"Mood sound",subtitle:"Copy emoji to press in your work or project"
        ,link:"/mood",icon:"mdi-music-note-outline"
      },
      {
        title:"Timer",subtitle:"Copy emoji to press in your work or project"
        ,link:"/timer",icon:"mdi-alarm"
      },
      {
        title:"Special font",subtitle:"Copy emoji to press in your work or project"
        ,link:"/emoji/font",icon:"mdi-function"
      },
      {
        title:"Code color products",subtitle:"Copy emoji to press in your work or project"
        ,link:"/word_color",icon:"mdi-license"
      },
      {
        title:"Abount me",subtitle:"Copy emoji to press in your work or project"
        ,link:"/abount",icon:"mdi-license"
      }
      ,{
        title:"Pomodoro",subtitle:"Copy emoji to press in your work or project"
        ,link:"/timer/pomodoro",icon:"mdi-license"
      }]
    }
  }
}
</script>