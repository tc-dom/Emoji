<template>
    <div>
        <h1>{{ mycolor }}</h1>
  <button @click="generator">New Color</button>
  
  <p><a href="https://enotcode.com">Made with <i class="far fa-heart"></i> by enotcode</a></p>
    </div>
</template>
<script>
export default {
    data(){return{
         mycolor: '#'+(Math.random()*0xFFFFFF<<0).toString(16)
    }},
     mounted() {
     document.body.style.background = this.mycolor;
  },
    methods:{
         generator: function(){
        this.mycolor = '#'+(Math.random()*0xFFFFFF<<0).toString(16);
        document.body.style.background = this.mycolor;
      }
    }
}
</script>