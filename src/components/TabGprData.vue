<template>
  <div>
    <h3 class="text-3xl text-left text-semibold">Geo-positioned Images</h3>
    <p class="text-left text-sm leading-relaxed mt-4">
      WIP
    </p>
    <div class="bg-gray-50 block w-full p-6 my-6">
      <h4 class="text-semibold text-sm">Try it</h4>
      <h2 class="text-lg py-4">Show georeferenced images inside the model</h2>
          <Toggle v-model="galleryOpen" :classes="{
                        toggleOn: 'bg-indigo-600 border-indigo-500 justify-start text-white',
                        toggleOff: 'bg-gray-200 border-gray-200 justify-end text-gray-700'
                    }" v-on:change="toggleGallery"></Toggle>
        <span class="text-sm font-medium pl-4 block" v-if="galleryOpen">Hide GPR Data</span>
        <span class="text-sm font-medium pl-4 block" v-if="!galleryOpen">Show GPR Data</span>
    </div>


  </div>
</template>

<script>
import Toggle from '@vueform/toggle/dist/toggle.vue2.js'
export default {
  name: 'TabGprData',
  components:{
    Toggle
  },
  created: function () {
    //Close explosion if it was enabled;
    const iframe = document.getElementById('model-iframe');
    iframe.contentWindow.postMessage({func:"explode", value:0},"*");
    iframe.contentWindow.postMessage({func:"gallery", value:false},"*");
  },
  data(){
    return{
      galleryOpen:false,
    }
  },
  methods:{
    toggleGallery(val){
      const iframe = document.getElementById('model-iframe');
      iframe.contentWindow.postMessage({func:"gpr", value:val},"*");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
<style src="@vueform/toggle/themes/default.css"></style>
