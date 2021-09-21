<template>
  <div>
<!--    <h3 class="text-3xl text-left text-semibold">Model Explosion interactive effect</h3>-->
    <p class="text-left text-sm leading-relaxed mt-4">
      In order to facilitate the comprehension of the architectural design, an interactive 3D model explosion tool has
      been developed.
      </p>

    <div class="bg-gray-50 block w-full p-6 my-6">
      <h4 class="text-semibold text-sm">Try it</h4>
      <h2 class="text-lg py-4">Explode the 3D model by dragging the handle</h2>
      <Slider v-model="explosionCurrentStep" v-bind:tooltips="false" v-on:update="explodeModels"></Slider>
    </div>
    <p class="text-left text-sm leading-relaxed mt-4">
    During the viewer's parameters' setup, it is possible to define the axes toward which every single
      unit (point cloud) will move in the 3D space and the speed of the explosion effect. The different objects are
      hence 'decomposed,' and the construction features are highlighted. If enabled, a slider becomes available to the
      viewer. The interaction happens in real-time. Dragging the slider's knob forces each part of getting further away
      from the center of the scene according to the movement configured.
    </p>
  </div>
</template>

<script>
import Slider from '@vueform/slider/dist/slider.vue2.js'
export default {
  name: 'TabExplosion',
  components:{
    Slider
  },
    created: function () {
    //Close gallery if open
    const iframe = document.getElementById('model-iframe');
    iframe.contentWindow.postMessage({func:"gallery", value:false},"*");
    iframe.contentWindow.postMessage({func:"gpr", value:false},"*");
  },
  data() {
    return {
      explosionCurrentStep: 0,
    }
  },
  methods: {
    explodeModels: function () {
      //this.explosionCurrentStep = this.explosionCurrentStep + plusminus;
      const iframe = document.getElementById('model-iframe');
      iframe.contentWindow.postMessage({func:"explode", value:this.explosionCurrentStep},"*");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<style src="@vueform/slider/themes/default.css"></style>