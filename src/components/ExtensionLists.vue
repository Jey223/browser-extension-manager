<template>
    <section class="extension-section">
        <h1 class="h1-style" :class="darkMode ? 'lighth1' : 'darkh1'">Extension List</h1>
        <div class="wrap">
            <button :class="{activeButton('all')}" class="btn-margin" @click="handleClickAll('all')">All</button>
            <button :class="activeButton" class="btn-margin" @click="handleClickAll('active')">Active</button>
            <button :class="activeButton" class="btn-margin" @click="handleClickAll('inactive')">Inactive</button>
        </div>
    </section>
</template>

<script>

export default {
    props: {
        darkMode: {
            type:Boolean,
            required:false,
            default:false
        },
    },
    data(){
        return{
            isClicked: 'all',
        }
    },
    emits: ['filter-mode'],
    computed: {
        // activeButton(){
        //     return this.isClicked === 'active' ? this.buttonClick('active') : this.isClicked === 'inactive' ? this.buttonClick('inactive') : this.buttonClick('all')
            // if(this.isClicked === 'all'){
            //     console.log(this.buttonClick('all'))
            //     return this.buttonClick('all')
            // } else if (this.isClicked === 'active') {
            //     return this.buttonClick('active')
            // } else if (this.isClicked === 'inactive'){
            //     return this.buttonClick('inactive')
            // }
        },
            
        // button1Class(){
        //      return this.isClicked === 'allbtn'
        //     ? (this.darkMode ? 'active-dark' : 'active')
        //     : (this.darkMode ? 'btn-dark' : 'btn-light')
        // },
        //  button2Class(){
        //     return this.isClicked === 'activebtn'
        //     ? (this.darkMode ? 'active-dark' : 'active')
        //     : (this.darkMode ? 'btn-dark' : 'btn-light')
        // },
        // button3Class(){
        //     return this.isClicked === 'inactivebtn'
        //     ? (this.darkMode ? 'active-dark' : 'active')
        //     : (this.darkMode ? 'btn-dark' : 'btn-light')
        // },
    // },
    methods: {
        activeButton(mode){
           return  (mode)
            // ? (this.darkMode ? 'active-dark' : 'active')
            // : (this.darkMode ? 'btn-dark' : 'btn-light')
        },

        handleClickAll(mode){
           this.isClicked = mode;
           this.$emit('filter-mode', mode) 
           this.activeButton(this.isClicked)
        },
    }
}
</script>


<style scoped>
    .extension-section {
        margin: 33px 0px;
        display: flex;
        flex-wrap:wrap;
        justify-content: space-between;
        align-items: center;
    }
    .h1-style{
        /* color: hsl(227, 75%, 14%); */
        font-size: 30px;
        margin: 0;
    }
    .darkh1{
        color: hsl(227, 75%, 14%);
    }
    .lighth1{
        color:hsl(200, 60%, 99%);
    }
    .wrap{
        display: flex;
        gap:0.5rem
    }
    .btn-margin{
        padding: 7px 15px;
        border-radius: 30px;
        border: none;
        font-size: 16px;
        cursor: pointer;
        flex: 1;
    }
    .btn-margin:focus{
        border:1px solid hsl(3, 71%, 56%);
    }
    .btn-light{
        background-color: hsl(200, 60%, 99%);
        box-shadow:0 1.5px 5px hsl(217, 61%, 90%);
        color:hsl(227, 75%, 14%);
    }
    .btn-light:hover{
        background-color: hsl(20, 60%, 99%);
    }
    .btn-dark{
        background-color:hsl(225, 23%, 24%);
        color: hsl(200, 60%, 99%);
        border: 1px solid hsl(226, 11%, 37%);
    }
    .btn-dark:hover{
        background-color:hsl(226, 11%, 37%);
    }
    
    .active {
        background-color: hsl(3, 77%, 44%);
        color: hsl(200, 60%, 99%);
    }
    .active:hover{
        background-color:hsl(3, 86%, 64%);
    }
    .active-dark{
        background-color: hsl(3, 71%, 56%);
    }
    .active-dark:hover{
        background-color:hsl(3, 77%, 44%);
    }
    @media (max-width: 470px ) {
        .extension-section{
            justify-content: center;
            align-items: center;
            gap:1rem;
        }
        .extension-section h1{
        font-size: 30px;
        }
    }
</style>