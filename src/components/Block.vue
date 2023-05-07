<template>
  <div class="block" @click="handleClickBlock">
    Click me
  </div>
</template>

<script>
export default {
  name: 'Block',
  data() {
    return {
      timer: null,
      reactionTimer: 0,
    }
  },
  mounted() {
    this.startTimer()
  },
  methods: {
    handleClickBlock() {
      this.stopTimer()
      this.$emit('end', this.reactionTimer)
    },
    startTimer() {
      let startTime = Date.now();
      this.timer = setInterval(() => {
          var elapsedTime = Date.now() - startTime;
          this.reactionTimer = (elapsedTime / 1000).toFixed(3);
      }, 100);
    },
    stopTimer() {
      clearInterval(this.timer)
    }
  }
}
</script>


<style scoped>
.block {
  width: 400px;
  height: 200px;
  margin: 50px auto;
  background: #039C88;
  color: #FFFFFF;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
}

</style>