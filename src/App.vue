<template>
    <section class="lightBody">
      <TheHeader />
      <ExtensionLists />
      <div class="card-section">
        <ExtensionCard 
          v-for="extension in extensions"
          :key="extension.name"
          :id="extension.name"
          :logo="extension.logo"
          :name="extension.name"
          :description="extension.description"
          :isactive="extension.isActive"
          @toggle-is-active="toggleActiveStatus" />
      </div>
      
    </section>
</template>

<script>
import ExtensionCard from './components/ExtensionCard.vue';
import ExtensionLists from './components/ExtensionLists.vue';
import TheHeader from './components/TheHeader.vue';
// import data from '../src/data.json'

export default {
  components: {
    TheHeader,
    ExtensionLists,
    ExtensionCard,
  },
  data(){
    return {
      extensions : [
      {
          "logo": require("./assets/images/logo-devlens.svg"),
          "name": "DevLens",
          "description": "Quickly inspect page layouts and visualize element boundaries.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-style-spy.svg"),
          "name": "StyleSpy",
          "description": "Instantly analyze and copy CSS from any webpage element.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-speed-boost.svg"),
          "name": "SpeedBoost",
          "description": "Optimizes browser resource usage to accelerate page loading.",
          "isActive": false
      },
      {
          "logo": require("./assets/images/logo-json-wizard.svg"),
          "name": "JSONWizard",
          "description": "Formats, validates, and prettifies JSON responses in-browser.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-tab-master-pro.svg"),
          "name": "TabMaster Pro",
          "description": "Organizes browser tabs into groups and sessions.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-viewport-buddy.svg"),
          "name": "ViewportBuddy",
          "description": "Simulates various screen resolutions directly within the browser.",
          "isActive": false
      },
      {
          "logo": require("./assets/images/logo-markup-notes.svg"),
          "name": "Markup Notes",
          "description": "Enables annotation and notes directly onto webpages for collaborative debugging.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-grid-guides.svg"),
          "name": "GridGuides",
          "description": "Overlay customizable grids and alignment guides on any webpage.",
          "isActive": false
      },
      {
          "logo": require("./assets/images/logo-palette-picker.svg"),
          "name": "Palette Picker",
          "description": "Instantly extracts color palettes from any webpage.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-link-checker.svg"),
          "name": "LinkChecker",
          "description": "Scans and highlights broken links on any page.",
          "isActive": true
      },
      {
          "logo": require("./assets/images/logo-dom-snapshot.svg"),
          "name": "DOM Snapshot",
          "description": "Capture and export DOM structures quickly.",
          "isActive": false
      },
      {
          "logo": require("./assets/images/logo-console-plus.svg"),
          "name": "ConsolePlus",
          "description": "Enhanced developer console with advanced filtering and logging.",
          "isActive": true
      }
    ]
    }
  },
  methods: {
    toggleActiveStatus(extensionId){
      const identifiedExtension = this.extensions.find((extension) => extension.name === extensionId);
      identifiedExtension.isActive = !identifiedExtension.isActive
      console.log(identifiedExtension.isActive)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100..900&display=swap');

*, *::before, *::after{
  box-sizing: border-box;
}
body {
  background: linear-gradient(180deg, #EBF2FC 0%, #EEF8F9 100%); 
  font-family: "Noto Sans", sans-serif;
  margin: 0;
}

.card-section{
  display: flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  margin-top: 15px;

}
#app {
  width: 90%;
  padding: 30px 0;
  margin: 0 auto;
}

</style>
