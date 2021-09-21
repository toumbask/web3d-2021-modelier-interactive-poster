<template>
  <iframe id="model-iframe" :src="url" width="100%" height="100%" onload="" style="height: 100vh">

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
