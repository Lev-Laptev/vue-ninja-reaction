<template>
  <div
    class="block" 
    v-if="showBlock" 
    @click="stopTimer"
  >
    Click me
  </div>
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
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 300px;

  margin: 40px auto;
  padding: 100px 0;

  color: #ffffff;
  
  background-color: #0faf87;
  border-radius: 20px;
  text-align: center;
}
</style>