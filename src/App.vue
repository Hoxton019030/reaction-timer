<template>
  <h1>Hoxton Reaction</h1>
  <button @click="start" :disabled="isPlaying">開始遊玩</button>
  <BlockDiv v-if="isPlaying" v-bind:delay="delay" ></BlockDiv>
</template>

<script>
import BlockDiv from "./components/BlockDiv.vue";
export default {
  name: "App",
  components: { BlockDiv },
  data() {
    return {
      isPlaying: false,
      delay: null,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
      console.log(this.isPlaying)
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
