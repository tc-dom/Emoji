<template>
  <div>
    <v-list v-for="emoji in emogies" :key="emoji">
      <v-list-item v-for="e in emoji" :key="e.name">
        <v-list-item-icon><span class="emoji">{{ e.char }}</span></v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>{{ e.name }}</v-list-item-title>
          <v-list-item-subtitle>
            {{e.category}}
            {{e.subgroup}}
          </v-list-item-subtitle>
        </v-list-item-content>
        <v-list-item-action> <v-btn icon>
          <v-icon>
            mdi-content-copy
          </v-icon>
          </v-btn></v-list-item-action>
      </v-list-item>
    </v-list>
  

    <v-btn @click="fetch()">Refresh Data</v-btn>
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
    async getNextUser() {
      window.onscroll = () => {
        let bottomOfWindow =
          document.documentElement.scrollTop + window.innerHeight ===
          document.documentElement.offsetHeight;
        if (bottomOfWindow) {
          this.page = this.page + 1;
          this.fetch(this.page);
          console.log("Scroll");
        }
      };
    },
    async fetch(page) {
      Promise.all([
        fetch("/emoji/emoji" + this.page + ".json").then(
          (res) => (res.ok && res.json()) || Promise.reject(res)
        ),
      ]).then((data) => {
        this.emogies.push(data[0]);
        console.log(data[0]);
      });
    },
  },
  mounted() {
    this.getNextUser();
  },
};
</script>
<style scoped>
li {
  margin-bottom: 0.5rem;
}
li:first-letter {
  text-transform: uppercase;
}
.loading {
  display: inline-block;
  min-width: 1.5rem;
  height: 1.5rem;
  border: 4px solid rgba(9, 133, 81, 0.705);
  border-radius: 50%;
  border-top-color: #158876;
  animation: spin 1s ease-in-out infinite;
}
.list {
  width: 100%;
}
.emoji {
  font-size: 60px;
  border-radius: 10px;
  display: inline-block;
  margin: 5px;
  text-align: center;
  min-width: 80px;
}
.emojo {
  min-width: 122px;
}
@keyframes spin {
  to {
    -webkit-transform: rotate(360deg);
  }
}
</style>
