<template>
  <div class="block" v-show="showBlock" @click="stopTimer"></div>
</template>

<script>
export default {
  props: ["delay"],
  emits: ["end"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      totalPoints: 0,
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
      // start the timer, tick every 10ms
      this.timer = setInterval(() => {
        this.reactionTime += 10;
        if (this.reactionTime > 2000) {
          this.totalPoints = 0;
        } else {
          this.totalPoints = -this.reactionTime / 2 + 1000;
        }
      }, 10);
    },
    stopTimer() {
      // stop the timer
      clearInterval(this.timer);
      this.$emit("end", {
        reactionTime: this.reactionTime,
        totalPoints: this.totalPoints,
      });
    },
  },
};
</script>

<style>
.block {
  border-radius: 20px;
  background-image: url("../assets/img/cow_cowboy.png");
  background-repeat: no-repeat;
  background-position: center;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
  height: 75px;
}
</style>