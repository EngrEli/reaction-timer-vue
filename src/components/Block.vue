<template>
  <div class="block" @click="handleClickBlock">
    Click me
  </div>
</template>

<script>
export default {
  name: 'Block',
  methods: {
    handleClickBlock() {
      this.$emit('handleClickBlock');
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