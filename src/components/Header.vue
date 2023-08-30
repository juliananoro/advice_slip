<template>
    <div id="header">
        <img src="../assets/logo.png" alt="logo do site">
        <h1>Fortune Teller</h1> 
    </div>
    
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
   #header {
    display: flex;
    justify-content: center;
    margin: 2% 2% 2% 2%;
   }
    img {
        width: 48px;
        height: 48px;
    }
    h1 {
        margin: 0px 0px 0px 16px;
        font-family: 'Rye', sans-serif;
        font-weight: normal;
        font-size: 40px;
    }
</style>