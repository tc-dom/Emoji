<template>
  <div id="app">
    <input 
           v-on:focus="$event.target.select()" 
           ref="clone" 
           readonly 
           :value="text"/>
    <button @click="copy">Copy</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: 'This will get copied!'
    };
  },
  methods: {
    copy() {
      this.$refs.clone.focus();
      document.execCommand('copy');
    }
  }
};
</script>