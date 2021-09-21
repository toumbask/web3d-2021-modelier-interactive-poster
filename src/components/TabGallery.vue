<template>
  <div>
    <h3 class="text-3xl text-left text-semibold">Images Gallery</h3>
    <p class="text-left mt-4">
      Besides the 3D models of each church, an extensive repository of 2D images has been created during the IH-AT
      project, including contemporary and historical ones.
      This database is currently available exploiting the same 3D web environment. The collection of images have been
      indeed uploaded through the administrator panel to generate an image gallery enriching the 3D visualization.

    </p>
        <div class="bg-gray-50 block w-full p-12">
      <h4 class="text-semibold text-sm">Try it</h4>
      <h2 class="text-lg py-4">Open the gallery and choose an image to auto-align the model. <br>Use the popup slider to adjust opacity.</h2>
          <Toggle v-model="galleryOpen" :classes="{
                        toggleOn: 'bg-indigo-600 border-indigo-500 justify-start text-white',
                        toggleOff: 'bg-gray-200 border-gray-200 justify-end text-gray-700'
                    }"></Toggle>
        <span class="text-sm font-medium pl-4 block" v-if="galleryOpen">Hide Gallery</span>
        <span class="text-sm font-medium pl-4 block" v-if="!galleryOpen">Show Gallery</span>
    </div>

    <p class="text-left mt-4">
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
  components:{
    Toggle
  },
  data(){
    return{
      galleryOpen:false,
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<style src="@vueform/toggle/themes/default.css"></style>
