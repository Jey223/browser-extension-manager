<template>
    <section class="extension-section">
        <h1 class="h1-style" :class="darkMode ? 'lighth1' : 'darkh1'">Extension List</h1>
        <div class="wrap">
            <button :class="button1Class" class="btn-margin" @click="handleClickAll('allbtn', 'all')">All</button>
            <button :class="button2Class" class="btn-margin" @click="handleClickAll('activebtn', 'active')">Active</button>
            <button :class="button3Class" class="btn-margin" @click="handleClickAll('inactivebtn', 'inactive')">Inactive</button>
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
            isClicked: 'allbtn',
        }
    },
    computed: {
        button1Class(){
             return this.isClicked === 'allbtn'
            ? (this.darkMode ? 'active-dark' : 'active')
            : (this.darkMode ? 'btn-dark' : 'btn-light')
        },
         button2Class(){
            return this.isClicked === 'activebtn'
            ? (this.darkMode ? 'active-dark' : 'active')
            : (this.darkMode ? 'btn-dark' : 'btn-light')
        },
        button3Class(){
            return this.isClicked === 'inactivebtn'
            ? (this.darkMode ? 'active-dark' : 'active')
            : (this.darkMode ? 'btn-dark' : 'btn-light')
        },
    },
    methods: {
        handleClickAll(buttonClicked, mode){
           this.isClicked = buttonClicked;
           this.$emit('filter-mode', mode) 
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