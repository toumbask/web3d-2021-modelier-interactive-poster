<template>
  <iframe :src="url" width="100%" height="500" onload="alert('myframe is loaded');">

  </iframe>
</template>

<script>
export default {
  name: 'ModelierIframe',
  props: {
    url: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
