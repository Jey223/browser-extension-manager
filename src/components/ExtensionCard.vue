<template>
        <div class="card" :class="darkMode ? 'card-dark' : 'card-light'"> 
            <div class="card-info">
                <div class="card-img" >
                    <img :src="extension.logo"/>
                </div>
                <div class="card-info-text">
                    <h2 :class="darkMode ? 'dark-mode-info' : 'light-mode-info'">{{ extension.name }}</h2>
                    <p :class="darkMode ? 'dark-mode-description' : 'light-mode-description'">{{extension.description}} </p>
                </div>
            </div>
            <div class="card-btns">
                <button class="remove" :class="darkMode ? 'remove-dark' : 'remove-light'" @click="handleRemoval">Remove</button>
                    <div class="button-switch">
                        <label class="switch">
                            <input type="checkbox" v-model="isActive" @change="changeExtensionValue()" />
                            <span class="toggle-active toggle-active-true" :class="[darkModeToggleActive, toggleActiveIsTrue]"></span>
                        </label>
                    </div>
            </div>
        </div>
</template>

<script>
export default {
    props: {
        extension: {
            type:Object,
            required: true,
        },
        darkMode: {
            type:Boolean,
            required:false,
            default:false
        },
    },
    data(){
        return {
            isActive: this.extension.isActive
        }
    },
    emits: ['remove-card', 'update'],
    computed: {
        darkModeToggleActive(){
            return {'toggle-active-dark toggle-active-darkmode' : this.darkMode}
        },
        toggleActiveIsTrue(){
            return {'toggle-active-true' : this.extension.isActive}
        },
    },
    methods: {
        handleRemoval(){
            this.$emit('remove-card', this.extension.name);
        },
        changeExtensionValue(){
            this.$emit('update', this.extension.name, this.isActive )
        }

    }
}

</script>

<style scoped>
    .card{
        flex-grow: 1;
        max-width: calc(33.3333% - 0.8rem);
        height: 250px;
        padding:20px;
        border-radius: 20px;
        margin-bottom: 5px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .card-light{
        background-color:hsl(200, 60%, 99%);
        box-shadow:0 1.5px 6px hsl(217, 61%, 90%);
    }
    .card-dark{
        background-color:hsl(226, 25%, 17%);
        border: 1px solid hsl(226, 11%, 37%);
    }
    .card-info {
        align-items: baseline;
        display: flex;
        flex-wrap: wrap;
        text-align: left;
        gap: 0.5rem;
        /* margin-bottom: 20px; */
    }
    .card-img  {
        margin-right: 10px;
        top:0px;
    }
    img{
        object-fit: cover;
        vertical-align: middle;
    }
    .card-info-text{
        flex: 1;
    }
    .card-info-text h2{
        margin: 0px;
        font-size: 20px;
    }
    .light-mode-info{
        color: hsl(227, 75%, 14%);
    }
    .dark-mode-info{
        color: hsl(0, 0%, 93%);
    }
    .card-info-text p{
        font-size: 16px;
    }
    .light-mode-description{
        color: hsl(226, 11%, 37%);
    }
    .dark-mode-description{
        color: hsl(217, 61%, 90%);
    }
    .card-btns{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .remove{
        padding: 7px 15px;
        border-radius: 30px;
        font-size: 15px;
        cursor: pointer;
    }
    .remove:focus{
        border:1px solid hsl(3, 77%, 44%);
    }
    .remove-light{
        color:hsl(227, 75%, 14%);
        border: 2px solid hsl(0, 0%, 93%) ;
        background-color: hsl(200, 60%, 99%);
    }
    .remove-light:hover{
        background-color: hsl(3, 77%, 44%);
    }
    .remove-dark{
        color:hsl(200, 60%, 99%) ;
        background-color:hsl(226, 25%, 17%);
        border: 1px solid hsl(226, 11%, 37%);
    }
    .remove-dark:hover{
        background-color:hsl(3, 71%, 56%);
    }
    .switch{
        position: relative;
        display: inline-block;
        width: 45px;
        height: 25px;
    }
    
    .switch input{
        opacity: 0;
        width: 0;
        height: 0;
    }
    .toggle-active{
        position: absolute;
        background-color: hsl(0, 0%, 78%);
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        transition: .4s;
        cursor: pointer;
        border-radius: 34px;
    }
   .toggle-active:focus{
        border:1px solid hsl(3, 71%, 56%);
        padding:2px;
    }
    .toggle-active-dark {
        background-color: hsl(226, 11%, 37%);
    }
    .toggle-active::before{
        position: absolute;
        content: "";
        height: 20px;
        width: 20px;
        left:3px;
        bottom:3px;
        background-color: hsl(200, 60%, 99%);
        transition: .4s;
        border-radius: 30px;
    }
    input:checked + .toggle-active {
        background-color:hsl(3, 77%, 44%);
    }
    input:checked + .toggle-active-true:hover {
        background-color:hsl(3, 71%, 56%);
    }
    input:checked + .toggle-active-darkmode{
        background-color:hsl(3, 71%, 56%);
    }
    input:checked + .toggle-active-darkmode:hover {
        background-color:hsl(3, 86%, 64%);
    }
    .button-switch:focus {
        border: 1px solid hsl(3, 86%, 64%);
    }
    input:checked + .toggle-active::before {
        transform: translateX(20px);
    }
    @media (max-width: 768px) {
        .card{
            max-width: calc(50% - 0.8rem);
        }
    }
     @media (max-width: 426px) {
        .card{
            max-width: 100%;
        }
    }
</style>