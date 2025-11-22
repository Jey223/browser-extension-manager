<template>
    <section class="header-section" :class="{darkHeader: darkMode}">
        <div class="logo">
            <img v-if="darkMode" class="logoImg" :src="require('../assets/images/logo.svg')" />
            <img v-else  :src="require('../assets/images/logo.svg')" />
        </div>
        <button class="mode-class" @click="toggleDarkMode" :class="toggleClasses">
             <img v-if="darkMode" src="../assets/images/icon-sun.svg" />
            <img v-else src="../assets/images/icon-moon.svg" />
        </button>
    </section>
</template>

<script>
    export default {
        computed: {
            toggleClasses(){
                if(this.darkMode){
                    return 'dark-toggle-mode'
                }else {
                     return 'light-toggle-mode'
                }
            }
        },
        data() {
            return {
                darkMode: false
            }
        },
        methods: {
            toggleDarkMode(){
                this.darkMode = !this.darkMode
                this.setDarkBody()
            },
            setDarkBody(){
                const body = document.body;
                body.classList.toggle('dark-body')
                console.log(body.className)
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
    .darkHeader{
        background-color:hsl(226, 25%, 17%);
         box-shadow:0 1px 0 hsl(225, 23%, 24%);
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
    .light-toggle-mode{
        background-color:hsl(0, 0%, 93%);
    }
    .dark-toggle-mode{
        background-color:hsl(225, 23%, 24%) ;
    }
    .light-toggle-mode:hover {
        background-color: hsl(0, 0%, 78%);
    }
    .dark-toggle-mode:hover{
        background-color:hsl(226, 11%, 37%) ;
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