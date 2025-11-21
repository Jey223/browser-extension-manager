<template>
    <section class="extension-section">
        <h1>Extension List</h1>
        <div class="wrap">
            <button class="btn-margin" id="all">All</button>
            <button class="btn-margin" id="active">Active</button>
            <button id="inactive">Inactive</button>
        </div>
    </section>
   
</template>

<script>

export default {
    components: {
    }
}
</script>


<style scoped>
    .extension-section {
        margin-top: 30px;
        display: flex;
        /* flex-wrap:wrap; */
        justify-content: space-between;
        align-items: center;
    }
    h1{
        color: hsl(227, 75%, 14%);
        font-size: 30px;
    }
    button{
        color:hsl(227, 75%, 14%);
        padding: 7px 15px;
        border-radius: 30px;
        border: none;
        background-color: hsl(200, 60%, 99%);
        box-shadow:0 1.5px 5px hsl(217, 61%, 90%);
        font-size: 15px;
        cursor: pointer;
    }
    .btn-margin{
        margin-right: 5px;
    }
</style>