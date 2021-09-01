<template>
  <div id="app">

    <div class="max-w-7xl mx-auto mt-8">
      <h1 class="text-extrabold underline text-2xl text-left">Our project tile goes here</h1>
      <TabbedContent v-bind:tabs="tabs" class="mt-4"></TabbedContent>

      <div class="grid grid-cols-3 gap-4 my-8">
      <div class="pr-8">
        <h3 class="text-3xl text-left text-semibold">Application Development Framework</h3>
        <p class="text-left mt-4">
          The platform is open-sourced and aims to work as a higher-level development framework to support the easier
          development of interactive tools for 3D model visualization on the web (Figure \ref{fig:developframework}).
          The IH-AT platform handles all the required processes for authorization and initialization purposes, isolating
          the steps needed to develop every single interactive tool.
          Docker.
        </p>
                <p class="text-left mt-4">
          This approach facilitates non-expert JavaScript
          users, without a-priori knowledge of the Back-end technologies, to customize the existing platform
          capabilities and add new interactive WebGL features.
          The IH-AT platform is currently pre-configured to be easily deployable in containerized environments using
          Docker.
        </p>
      </div>
      <!-- ... -->
      <div class="col-span-2">
        <ModelierIframe
          url="https://example.com"></ModelierIframe>

      </div>
    </div>

    </div>
  </div>
</template>

<script>
import './assets/tailwind.css';
import ModelierIframe from "./components/ModelierIframe";
import TabbedContent from "./components/TabbedContent";

export default {
  name: 'App',
  data() {
    return {
      tabs: [
        {name: 'General', href: '#', current: true},
        {name: 'Explosion', href: '#', current: false},
        {name: 'Gallery', href: '#', current: false},
        {name: 'Geoposition Data', href: '#', current: false},
        {name: 'Development Framework', href: '#', current: false},
      ]
    }
  },
  components: {
    ModelierIframe,
    TabbedContent
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
