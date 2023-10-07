<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  methods: {
    startTimer() {
     this.timer= setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log('反應時間'+this.reactionTime)
    },
  },
  // mounted: 當component載入時會觸發
  mounted() {
    console.log("component掛載");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
      console.log("延遲:" + this.delay);
    }, this.delay);
  },
  // data變動導致dom重新渲染時才會觸發，例如把showBlock的狀態改成true
  updated() {
    console.log("元件變動");
  },
  unmounted() {
    console.log("component卸載");
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: lightgreen;
  color: black;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>