<template>
  <div>
    <v-btn @click.stop="mojo = !mojo" class="ma-3">Copy button mode</v-btn>
    <p v-for="(emoji, i) in emogies" :key="i" class="text-center">
      <span v-for="e in emoji" :key="e.code" class="text-center">
        <h1 class="name-header" v-if="e.name === 'Header'">
          {{ e.char }}
        </h1>
        <span v-else class="emoji" :class="{ emojo: !mojo }">
          {{ e.char }}

          <v-btn v-if="!mojo">{{ e.char }} | Copy</v-btn>
        </span>
      </span>
    </p>

  
  </div>
</template>
<script>
export default {
  data() {
    return {
      emogies: [],
      data: [],
      page: 1,
      mojo: true,
      list: false,
    };
  },
    watch: {
    $route: "fetch"
  },
  created() {
    this.fetch();
  },

  methods: {
    async fetch() {
    console.log(this.$route.params.cate);
      const page = this.$route.params.cate
      await Promise.all([
        fetch("/emoji/emoji" + page + ".json").then(
          (res) => (res.ok && res.json()) || Promise.reject(res)
        ),
      ]).then((data) => {
        this.emogies.push(data[0]);
      });
    },
 
   
  },
  mounted(){
    
  }
 
};
</script>
