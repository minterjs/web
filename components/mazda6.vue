<template>
    <div class="mazda6-container">
        <h2>MAZDA6PLS</h2>
        <div class="nupls"><img src="/my.gif"/><br/>ну pls</div>
    </div>
</template>

<script>
    export default {
        name: "mazda6"
    }
</script>

<style scoped>
    .mazda6-container {
        background-image: url('/mazda6pls.jpg');
        min-height: 100vh;
        width: 100%;
        background-size: 100vw;
        position: relative;
    }

    .nupls {
        position: absolute;
        bottom: 3vh;
        right: 3vw;
        text-align: right;
    }

    h2 {
        font-size: 20vh;
        color: white;
    }
</style>
