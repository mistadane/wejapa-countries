<template>
    <div class="header">
        <img src="../assets/logo.png" alt="WeJapa Logo">
        <h1>Countries</h1>
    </div>
</template>


<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        width: 100%;
        height: 70px;
        background: #000;
        text-align: center;
    }

    img {
        height: 100%;
    }

    h1 {
        display: inline-block;
        color: #fff;
        position: relative;
        top: -20px;
    }
</style>