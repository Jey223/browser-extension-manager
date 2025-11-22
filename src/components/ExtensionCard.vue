<template>
        <div class="card"> 
            <div class="card-info">
                <div class="card-img">
                    <img :src="logo"/>
                </div>
                <div class="card-info-text">
                    <h2>{{ name }}</h2>
                    <p>{{description}} </p>
                </div>
            </div>
            <div class="card-btns">
                <button class="remove">Remove</button>
                <!-- <button class="button-switch" > -->
                    <div class="button-switch">
                        <label class="switch">
                            <input type="checkbox" v-model="isChecked" />
                            <span class="slider"></span>
                        </label>
                    </div>
                    
                <!-- </button> -->
            </div>
        </div>
</template>

<script>
export default {
    props: {
        id:{
            type:String,
            required:true,
        },
        logo: {
            type:String,
            required: true,
        },
        name:{
            type:String,
            required:true,
        },
        description:{
            type:String,
            required:true,
        },
        isActive: {
            type:Boolean,
            required:false,
            default:true,
        }
    },
    emits: ['toggle-is-active'],
    data(){
        return{
            isChecked: false,
            data: ''
        }
    },
    watch: {
        isChecked(){
            this.toggleIsActive()
        }    
    },
    methods: {
        toggleIsActive(){
             this.$emit('toggle-is-active', this.id)
        }
    }
}

</script>

<style scoped>
    .card{
        flex-grow: 1;
        width: calc(33.3333% - 0.8rem);
        padding:20px;
        background-color:hsl(200, 60%, 99%);
        border-radius: 20px;
        box-shadow:0 1.5px 6px hsl(217, 61%, 90%);
        margin-bottom: 5px;
    }
    .card-info {
        display: flex;
        flex-wrap: wrap;
        text-align: left;
        gap: 0.5rem;
        margin-bottom: 20px;
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
        color: hsl(227, 75%, 14%);
        margin: 0px;
        font-size: 20px;
    }
    .card-info-text p{
        color: hsl(226, 11%, 37%);
        font-size: 16px;
    }
    .card-btns{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .remove{
        color:hsl(227, 75%, 14%);
        padding: 7px 15px;
        border-radius: 30px;
        border: 2px solid hsl(0, 0%, 93%) ;
        background-color: hsl(200, 60%, 99%);
        font-size: 15px;
        cursor: pointer;
    }
    /* .button-switch:focus{
        border: 1px solid black;
        padding: 2px;
        border-radius: 34px;
    } */
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
    .slider{
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
    .slider::before{
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
    input:checked + .slider {
        background-color:hsl(3, 77%, 44%);
    }
    .button-switch:focus {
        border: 1px solid hsl(3, 71%, 56%);
    }
    input:checked + .slider::before {
        transform: translateX(20px);
    }
    @media (max-width: 768px) {
        .card{
            width: calc(50% - 0.8rem);
        }
    }
     @media (max-width: 426px) {
        .card{
            width: 100%;

        }
    }
</style>