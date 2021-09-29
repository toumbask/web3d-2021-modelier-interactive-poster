<template>
  <div id="app">
    <!-- This example requires Tailwind CSS v2.0+ -->
    <div class="fixed z-10 inset-0 overflow-y-auto" aria-labelledby="modal-title" role="dialog" aria-modal="true"
         v-if="introOpen">
      <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
        <!--
          Background overlay, show/hide based on modal state.

          Entering: "ease-out duration-300"
            From: "opacity-0"
            To: "opacity-100"
          Leaving: "ease-in duration-200"
            From: "opacity-100"
            To: "opacity-0"
        -->
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>

        <!-- This element is to trick the browser into centering the modal contents. -->
        <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>

        <!--
          Modal panel, show/hide based on modal state.

          Entering: "ease-out duration-300"
            From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            To: "opacity-100 translate-y-0 sm:scale-100"
          Leaving: "ease-in duration-200"
            From: "opacity-100 translate-y-0 sm:scale-100"
            To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
        -->
        <div
            class="inline-block align-bottom bg-white rounded-lg px-4 pt-5 pb-4 text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-2xl sm:w-full sm:p-6">
          <div>
            <div class="mt-3 text-center sm:mt-5">
              <h3 class="text-lg leading-6 font-medium text-gray-900" id="modal-title">
                Invisible Heritage - Analysis and Technology Digital
                Platform
              </h3>
              <div class="mt-2">
                <p class="text-normal text-gray-500 tracking-tighter">
                  In an era of rapid technological improvements, <span class="font-semibold">state-of-the-art methodologies and tools dedicated to
                  protecting and promoting our cultural heritage</span> should be developed and extensively employed to
                  expand and
                  enrich historical and archaeological research and possibly revise or add new information to
                  established
                  theories. </p>
                <p class="text-normal text-gray-500  tracking-tighter mt-4">
                  <span class="font-semibold">The Invisible Heritage – Analysis and Technology (IH-AT)</span> project
                  aimed to design and develop a
                  portal comprised of reliable and efficient technology-ready tools for the visualization,
                  documentation, and
                  analysis of the UNESCO listed churches in the Troodos area of Cyprus applying geophysics, 3D modeling
                  techniques, and visualization methods, supported by art-historical and archaeological research.
                </p>
              </div>
            </div>
          </div>
          <div class="mt-5 sm:mt-6">
            <button type="button"
                    v-on:click="toggleIntro"
                    class="inline-flex justify-center w-full rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:text-sm">
              Check the IHAT Platform features
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="grid grid-cols-3 gap-0" style="height: 100vh;">
      <div class="flex flex-col justify-end content-end items-end px-8 py-1 fixed right-0 top-0">
          <h1 class="text-extrabold underline text-normal text-right text-gray-200">Invisible Heritage - Analysis and
            Technology Digital
            Platform
          </h1>
          <button type="button"
                  v-on:click="toggleIntro"
                  class="inline-flex justify-center bg-gray-200 rounded-md border border-transparent shadow-sm px-4 py-2 text-base font-medium gray-700 hover:text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:text-sm">
            Show intro
          </button>

        </div>
      <div class="flex flex-col overflow-auto">
        <div class="px-8 bg-gray-200">
          <div class="block w-fulltext-center font-semibold color-gray-600 mt-8 ">Features</div>
          <TabbedContent v-bind:tabs="tabs" v-bind:current="current" v-on:tab-selected="current = $event"
                         class="mt-4"></TabbedContent>
        </div>
        <div class="overflow-y-auto px-8 pb-12 bg-gray-200">
          <TabGeneral v-if="current === 'general' ">Intro</TabGeneral>
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
import TabGeneral from "./components/TabGeneral";
import TabExplosion from "./components/TabExplosion";
import TabGprData from "./components/TabGprData";
import TabDevelopmentFramework from "./components/TabDevelopmentFramework";
import TabGallery from "./components/TabGallery";

export default {
  name: 'App',
  data() {
    return {
      tabs: [
        {name: 'General', href: '#', id: "general"},
        {name: 'Explosion', href: '#', id: "explosion"},
        {name: 'Gallery', href: '#', id: "gallery"},
        {name: 'Geo-positioned Images', href: '#', id: "gprdata"},
        {name: 'Development Framework', href: '#', id: "devframework"},
      ],
      current: 'general',
      introOpen: true
    }
  },
  components: {
    ModelierIframe,
    TabbedContent,
    TabGeneral,
    TabExplosion,
    TabGallery,
    TabGprData,
    TabDevelopmentFramework
  },
  methods: {
    toggleIntro() {
      this.introOpen = !this.introOpen;
    }
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
