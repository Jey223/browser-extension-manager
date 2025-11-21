<template>
    <section class="light-section" :class="{darkSection: !lightMode}">
        <div class="logo">
            <img v-if="lightMode" :src="require('../assets/images/' + logoSrc)" />
            <img v-else class="logoImg" :src="require('../assets/images/' + logoSrc)" />
        </div>
        <button @click="toggleDarkMode" :style="{backgroundColor : lightMode ? 'hsl(0, 0%, 93%)' : 'hsl(226, 11%, 37%)' }">
            <!-- <img v-if="lightMode" :src="require('../assets/images/' + sunIcon)" /> -->
            <img v-if="lightMode" src="../assets/images/icon-moon.svg" />
            <img v-else src="../assets/images/icon-sun.svg" />
        </button>
    </section>
</template>

<script>
    export default {
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
    .light-section {
        background-color:hsl(200, 60%, 99%);
        display: flex;
        justify-content: space-between;
        align-items:center;
        padding: 15px;
        border-radius: 20px;
        box-shadow:0 1.5px 4px hsl(217, 61%, 90%);
    }
    .darkSection{
        background-color:hsl(225, 23%, 24%);
    }
    button{
        padding:10px;
        border: none;
        border-radius: 10px;
        cursor: pointer;
    }
    img.logoImg{
        filter: invert(100%) hue-rotate(182deg) brightness(102%) ;
    }

</style>