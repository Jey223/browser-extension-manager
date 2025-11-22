<template>
    <section class="header-section" :class="{darkSection: !lightMode}">
        <div class="logo">
            <img v-if="lightMode" :src="require('../assets/images/' + logoSrc)" />
            <img v-else class="logoImg" :src="require('../assets/images/' + logoSrc)" />
        </div>
        <button class="mode-class" @click="toggleDarkMode" :style="{backgroundColor : lightMode ? 'hsl(0, 0%, 93%)' : 'hsl(226, 11%, 37%)' }">
            <img v-if="lightMode" src="../assets/images/icon-moon.svg" />
            <img v-else src="../assets/images/icon-sun.svg" />
        </button>
    </section>
</template>

<script>
    export default {
        computed: {
            
        },
        data() {
            return {
                logoSrc:'logo.svg',
                lightMode: true
            }
        },
        methods: {
            toggleDarkMode(){
                this.lightMode = !this.lightMode
            }
        }
    }
</script>

<style scoped>
    .header-section {
        background-color:hsl(200, 60%, 99%);
        display: flex;
        justify-content: space-between;
        align-items:center;
        padding: 15px;
        border-radius: 20px;
        box-shadow:0 1.5px 4px hsl(217, 61%, 90%);
        margin: 0px;
    }
    .darkSection{
        background-color:hsl(225, 23%, 24%);
    }
    img.logoImg{
        filter: invert(100%) hue-rotate(182deg) brightness(102%) ;
    }
    .logo img{
        width: 100%;
        object-fit: cover;
    }
    .mode-class{
        padding:10px;
        border: none;
        border-radius: 10px;
        cursor: pointer;
    }
    @media (max-width: 768px) {
        .header-section{
            width: 100%;
            padding: 10px;
        }
        .logo{
            width: 150px;
        }
        .mode-class img{
            width: 18px;
        }
        
    }
</style>