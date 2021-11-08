<template>
  <div class="relative">
    <iframe v-on:load="loadingFinished" id="model-iframe" :src="url" width="100%" height="100%" onload=""
            style="height: 100vh">

    </iframe>
    <div class="absolute left-0 top-0 right-0 bottom-0 bg-gray-100 flex flex-col items-center justify-center" v-if="!loaded">
      <span class="text-3xl">Loading 3d model...</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModelierIframe',
  props: {
    url: String
  },
  data() {
    return {
      loaded: false,
    }
  },
  methods: {
    loadingFinished() {
      this.loaded = true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
