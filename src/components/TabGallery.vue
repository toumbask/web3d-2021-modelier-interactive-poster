<template>
  <div>
    <!--    <h3 class="text-3xl text-left text-semibold">Images Gallery</h3>-->
    <div class="bg-gray-50 block w-full p-6 my-6">
      <h4 class="text-semibold text-sm">Try it</h4>
      <h2 class="text-lg py-4">Open the gallery and choose an image to auto-align the model. <br>Use the popup slider to
        adjust opacity.</h2>
      <Toggle v-model="galleryOpen" :classes="{
                        toggleOn: 'bg-indigo-600 border-indigo-500 justify-start text-white',
                        toggleOff: 'bg-gray-200 border-gray-200 justify-end text-gray-700'
                    }" v-on:change="toggleGallery"></Toggle>
      <span class="text-sm font-medium pl-4 block" v-if="galleryOpen">Hide Gallery</span>
      <span class="text-sm font-medium pl-4 block" v-if="!galleryOpen">Show Gallery</span>
    </div>
    <p class="text-left text-sm leading-relaxed mt-4">
      With the final goal to provide an immersive user experience, the 3D model of each church has been aligned,
      resembling the perspective of the historical picture displayed.
      Each image, when selected, is then rendered on top of the 3D scene. A slider has been implemented to change the
      opacity of the images, allowing the viewer to visualize both the image and the 3D scene simultaneously.
    </p>


  </div>
</template>

<script>
import Toggle from '@vueform/toggle/dist/toggle.vue2.js'

export default {
  name: 'TabGallery',
  components: {
    Toggle
  },
  created: function () {
    //Close explosion if it was enabled;
    const iframe = document.getElementById('model-iframe');
    iframe.contentWindow.postMessage({func: "explode", value: 0}, "*");
  },
  data() {
    return {
      galleryOpen: false,
    }
  },
  methods: {
    toggleGallery(val) {
      const iframe = document.getElementById('model-iframe');
      iframe.contentWindow.postMessage({func: "gallery", value: val}, "*");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<style src="@vueform/toggle/themes/default.css"></style>
