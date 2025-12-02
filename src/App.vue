<template>
    <section class="lightBody">
      <TheHeader 
      :dark-mode="darkMode" 
      @toggle-dark-mode="toggleDarkMode" />
      <ExtensionLists  
          @filter-mode="setFilter"          
          :dark-mode="darkMode" 
      />
          <!-- :filter-mode="filterMode" -->
      <div class="card-section" v-if="filteredCards.length">
        <ExtensionCard 
          v-for="extension in filteredCards"
          :key="extension.name"
          :extension = 'extension'
          :dark-mode="darkMode"
          @remove-card = "removeCard"
          @update = 'changeIsActiveState'
        />
      </div>
      
    </section>
</template>

<script>
import ExtensionCard from './components/ExtensionCard.vue';
import ExtensionLists from './components/ExtensionLists.vue';
import TheHeader from './components/TheHeader.vue';
import data from '../src/data.json'

export default {
  components: {
    TheHeader,
    ExtensionLists,
    ExtensionCard,
  },
  data(){
    return {
      extensions : data,
      darkMode: false,
      filterMode: "all",
    }
  },
  

  created () {
    const storedDarkMode = localStorage.getItem('extensiondarkMode');
      if(storedDarkMode === 'true'){
        this.darkMode = true
        this.setdarkBody(true)
      }  else if(storedDarkMode === 'false'){
        this.darkMode = false
        this.setdarkBody(false)
      }


    const storedData = localStorage.getItem('extensionlist')
        if(storedData){
          this.extensions = JSON.parse(storedData)
          
        } else {
          localStorage.setItem('extensionlist', JSON.stringify(this.extensions));
        }
  },


  computed:{
    filteredCards(){
        if(this.filterMode === 'active'){
          return this.extensions.filter(card => card.isActive === true);
        } 
        if (this.filterMode === 'inactive'){
          return this.extensions.filter(card => card.isActive === false);
        }  
        return this.extensions;
    }
  },
 
  methods: {
    changeIsActiveState(name, isActive){
      const extensionName = this.extensions.find((extension) => extension.name === name);
      if (extensionName){
        extensionName.isActive = isActive
      }
    localStorage.setItem('extensionlist', JSON.stringify(this.extensions));
    },

    setFilter(type){
      this.filterMode = type;
    },
    toggleDarkMode(){
      this.darkMode = !this.darkMode
      this.setdarkBody(this.darkMode)
      localStorage.setItem('extensiondarkMode', this.darkMode)
    },
    setdarkBody(dark){
      dark ? document.body.classList.add('dark-body') : document.body.classList.remove('dark-body')
    },
    removeCard(name){
      this.extensions = this.extensions.filter(extension =>
         extension.name !== name)
      localStorage.setItem('extensionlist', JSON.stringify(this.extensions));
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
  min-height: 100vh;
}
.dark-body {
        background: linear-gradient(180deg, #040918 0%, #091540 100%);
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
