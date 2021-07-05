<template>
  <div class="block" v-if="showBlock" @click="stopTimer" :style="{marginLeft: randomPositionX + 'px', marginTop: randomPositionY + 'px'}">
    Click me
  </div>
</template>

<script>
export default {
  props: {
    delay: Number
  },
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      randomPositionX: null,
      randomPositionY: null,
      mousePoistionX: null
    }
  },
  mounted() {
    this.randomPositionX = this.getRandomNumber()
    this.randomPositionY = this.getRandomNumber()
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    },
    getRandomNumber() {
      return Math.random() * 100 + 100 * Math.round(Math.random())
    }
  }
}
</script>

<style scoped>
  .block {
    width: 150px;
    height: 150px;
    border-radius: 20px;
    background-color: #26be9e;
    color: #fff;
    text-align: center;
    line-height: 150px;
    cursor: pointer;
  }
</style>