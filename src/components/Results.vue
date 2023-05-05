<template>
  <div>
    <div>
      Reaction Time - {{ seconds }}
    </div>
    <h2>{{ resultsText }}</h2>
  </div>
  
</template>

<script>
export default {
  name: 'Results',
  props: {
    resultsText: String,
    seconds: Number
  }
}
</script>