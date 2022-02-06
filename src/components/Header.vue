<template>
    <div id="header">
        <header>
            <h1>Vue Nutri</h1>
        </header>
    </div>
</template>

<script>
    export default{
        name: 'header',
        data(){

        }
    }
</script>


<style scoped>
#header{
    display: flex;
    width: 100%;
    color: #fff;
}
header{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80px;
    width: 100%;
    background-color: #4c89e3;
    
}
</style>