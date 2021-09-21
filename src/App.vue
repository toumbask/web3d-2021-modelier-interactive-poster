<template>
  <div id="app">
      <div class="grid grid-cols-3 gap-0" style="height: 100vh;">
        <div class="flex flex-col overflow-auto">
          <div class="flex-shrink px-8 my-8">
            <h1 class="text-extrabold underline text-2xl text-left">Invisible Heritage - Analysis and Technology Digital Platform</h1>
            <p class="text-left text-normal mt-8">Intro text goes here</p>
          </div>
          <div class="px-8 my-8">
            <div class="block w-fulltext-center font-semibold color-gray-600 mt-8 ">Features</div>
            <TabbedContent v-bind:tabs="tabs" v-bind:current="current" v-on:tab-selected="current = $event" class="mt-4"></TabbedContent>
          </div>
          <div class="overflow-y-auto px-8 my-8">
            <div class="mt-8"></div>

    <!--        <TabGeneral v-if="current === 'general' ">Now you see me</TabGeneral>-->
            <TabExplosion v-if="current === 'explosion' "></TabExplosion>
            <TabGallery v-if="current === 'gallery' "></TabGallery>
            <TabGprData v-if="current === 'gprdata' "></TabGprData>
            <TabDevelopmentFramework v-if="current === 'devframework'"></TabDevelopmentFramework>
          </div>
        </div>
        <!-- ... -->
        <div class="col-span-2">
          <ModelierIframe
            url="https://modelier.us.aldryn.io/models/13e7c708-4b03-40d0-93b5-d94f45629046/v2/embed/"></ModelierIframe>

        </div>
    </div>
  </div>
</template>

<script>
import './assets/tailwind.css';
import ModelierIframe from "./components/ModelierIframe";
import TabbedContent from "./components/TabbedContent";
//import TabGeneral from "./components/TabGeneral";
import TabExplosion from "./components/TabExplosion";
import TabGprData from "./components/TabGprData";
import TabDevelopmentFramework from "./components/TabDevelopmentFramework";
import TabGallery from "./components/TabGallery";

export default {
  name: 'App',
  data() {
    return {
      tabs: [
        // {name: 'General', href: '#', id:"general"},
        {name: 'Explosion', href: '#', id:"explosion"},
        {name: 'Gallery', href: '#', id:"gallery"},
        {name: 'Geo-positioned Images', href: '#', id:"gprdata"},
        {name: 'Development Framework', href: '#', id:"devframework"},
      ],
      current: 'general'
    }
  },
  components: {
    ModelierIframe,
    TabbedContent,
    //TabGeneral,
    TabExplosion,
    TabGallery,
    TabGprData,
    TabDevelopmentFramework
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
</style>
