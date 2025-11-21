<template>
  <!-- <div class="body-section"> -->
    <section class="lightBody">
      <TheHeader />
      <ExtensionLists />
      <ul>
        <ExtensionCard 
          v-for="extension in extensions"
          :key="extension.name"
          :id="extension.name"
          :logo="extension.logo"
          :name="extension.name"
          :description="extension.description"
          :isactive="extension.isActive"
          @toggle-is-active="toggleActiveStatus" />
      </ul>
      
    </section>
  <!-- </div> -->
</template>

<script>
import ExtensionCard from './components/ExtensionCard.vue';
import ExtensionLists from './components/ExtensionLists.vue';
import TheHeader from './components/TheHeader.vue';

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
        // console.log(identifiedExtension.isActive = !identifiedExtension.isActive)
    }
  }
  
}
</script>

<style>
*{
  box-sizing: border-box;
}
body {
  background: linear-gradient(180deg, #EBF2FC 0%, #EEF8F9 100%); 
}
section {
  width: 93%;
  margin: 0 auto;
}
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale; */
  /* text-align: center; */
  color: #2c3e50;
  background: linear-gradient(180deg, #EBF2FC 0%, #EEF8F9 100%); 
  padding: 30px 0;
}
#app ul{
  margin: 15px auto 0 auto;
  padding: auto;
  list-style: none;
  width:93%;
  display:flex;
  flex-wrap: wrap;
  gap: 0.8rem;
  width:100%;
  margin-top: 15px;
}
</style>
