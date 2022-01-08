<template>
  <v-sheet max-width="1000" class="ma-2 mx-auto">
    <v-row>
      <v-col v-for="mood in moods" :key="mood.title">
        <v-sheet class="mood-box pa-5 mx-auto mt-3" outlined width="220" height="220">
      <p>{{mood.title}}</p>
      <v-icon large class="mood-btn">{{mood.icon}}</v-icon>
     <v-sheet>
       <v-slider
        v-model="value"
        step="10"
        thumb-label
        ticks
      ></v-slider>
     </v-sheet>
       <v-progress-linear
        :active="loading"
         :indeterminate="loading"
       rounded
      
      color="yellow darken-2"
    ></v-progress-linear>
    </v-sheet>
      </v-col>
    </v-row>
  </v-sheet>
</template>
<script>
export default {
  data(){
    return{
      loading: false,
      value:60,
      moods:[
        {icon:"mdi-weather-pouring",title:"Rain"},
        {icon:"mdi-weather-night-partly-cloudy",title:"Night"},
        {icon:"mdi-train",title:"Train"},
        {icon:"mdi-waves",title:"Sea"},
        {icon:"mdi-sail-boat",title:"Boat"},
        {icon:"mdi-airplane",title:"Plane"},
        {icon:"mdi-highway",title:"Traffic"},
        {icon:"mdi-weather-lightning",title:"Lightning"},
        {icon:"mdi-city-variant-outline",title:"City"},
        {icon:"mdi-keyboard-variant",title:"Keyboard"},
        {icon:"mdi-book-open-page-variant-outline",title:"Library"},
        {icon:"mdi-weather-windy-variant",title:"Windy"},
        {icon:"mdi-window-closed-variant",title:"Windows"},
        {icon:"mdi-weather-night",title:"Cricket"},
        {icon:"mdi-bird",title:"Bird"},
        {icon:"mdi-paw",title:"Wolf"},
        {icon:"mdi-walk",title:"Step walk"},
        {icon:"mdi-bugle",title:"Horn"},
        {icon:"mdi-alarm",title:"Clock"},
        {icon:"mdi-fan",title:"Fan"},
        {icon:"mdi-fire",title:"Fire"},
        {icon:"mdi-school-outline",title:"School"},
        {icon:"mdi-shaker-outline",title:"Cooking"},
        {icon:"mdi-water-outline",title:"Drop"},
        {icon:"mdi-wave",title:"Wave"}
      ]
    }
  }
}
</script>
<style>

.mood-box{
  border-radius: 25px !important;
}
.mood-btn{
  display: block !important;
  margin: auto !important;
  text-align: center;
  height: 100px;
}
i.mood-btn{
  font-size: 70px !important;
}
</style>