<template>
  <div id="app">

    <div class="max-w-7xl mx-auto mt-8">
      <h1 class="text-extrabold underline text-2xl text-left">Invisible Heritage - Analysis and Technology Digital Platform</h1>
      <TabbedContent v-bind:tabs="tabs" v-bind:current="current" v-on:tab-selected="current = $event" class="mt-4"></TabbedContent>

      <div class="grid grid-cols-3 gap-4 my-8">
      <div class="pr-8">
        <TabGeneral v-if="current === 'general' ">Now you see me</TabGeneral>
        <TabExplosion v-if="current === 'explosion' "></TabExplosion>
        <TabGallery v-if="current === 'gallery' "></TabGallery>
      </div>
      <!-- ... -->
      <div class="col-span-2">
        <ModelierIframe
          url="https://modelier.us.aldryn.io/models/b57f1cb0-5d7e-412f-bfec-391eb70c2735/v2/embed/"></ModelierIframe>

      </div>
    </div>

    </div>
  </div>
</template>

<script>
import './assets/tailwind.css';
import ModelierIframe from "./components/ModelierIframe";
import TabbedContent from "./components/TabbedContent";
import TabGeneral from "./components/TabGeneral";
import TabExplosion from "./components/TabExplosion";
import TabGallery from "./components/TabGallery";

export default {
  name: 'App',
  data() {
    return {
      tabs: [
        {name: 'General', href: '#', id:"general"},
        {name: 'Explosion', href: '#', id:"explosion"},
        {name: 'Gallery', href: '#', id:"gallery"},
        {name: 'Geoposition Data', href: '#', id:"gprdata"},
        {name: 'Development Framework', href: '#', id:"devframework"},
      ],
      current: 'general'
    }
  },
  components: {
    ModelierIframe,
    TabbedContent,
    TabGeneral,
    TabExplosion,
    TabGallery
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
