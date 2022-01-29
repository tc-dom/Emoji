<template>
  <div id="tc-dom">
    <p v-for="(emoji, i) in emogies" :key="i" class="text-center">
      <span v-for="e in emoji" :key="e.code" class="text-center">
        <v-sheet class="name-header" outlined v-if="e.name === 'Header'">
          <h1>{{ e.char }}</h1>
        </v-sheet>
        <span v-else class="emoji" :class="{ emojo: !mojo }">
          {{ e.char }}

          <v-btn v-if="!mojo">{{ e.char }} | Copy</v-btn>
        </span>
      </span>
    </p>

    <v-btn block v-if="page <= 17" @click="morefetch(page + 1)">Load next emoji</v-btn>
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

  created() {
    this.fetch(this.page);
  },
  methods: {
    async getNextData() {
      window.onscroll = () => {
        let bottomOfWindow =
          document.getElementById("tc-dom").scrollTop + window.innerHeight ===
          document.getElementById("tc-dom").offsetHeight;
        console.log(
          document.getElementById("tc-dom").scrollTop + window.innerHeight ===
            document.getElementById("tc-dom").offsetHeight
        );
        if (bottomOfWindow) {
          this.page = this.page + 1;
          this.fetch(this.page);
        }
      };
    },
    async fetch(page) {
      await Promise.all([
        fetch("/emoji/emoji" + page + ".json").then(
          (res) => (res.ok && res.json()) || Promise.reject(res)
        ),
      ]).then((data) => {
        this.emogies.push(data[0]);
      });
    },
    morefetch(page) {
      this.page = page;
      this.fetch(page);
    },
  },
  mounted() {
    this.getNextData();
    const $div = document.getElementById("tc-dom");

    console.log("CLIENT HEIGHT ", $div.scrollTop + window.innerHeight);
    console.log("SCROLL HEIGHT ", $div.scrollTop);
    console.log("OFFSET HEIGHT ", $div.offsetHeight);
  },
};
</script>
