<template>
    <div class="mazda6-container">
        <h2>MAZDA6PLS</h2>
        <p v-on:click="copy" class="how-to">Buy and delegate MAZDA6PLS or donate: Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37</p>
        <div class="nupls"><img src="/my.gif"/><br/>ну pls</div>
    </div>
</template>

<script>
    import copy from 'copy-to-clipboard';
    export default {
        name: "mazda6",
        methods: {
            copy() {
                copy('Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37');
                alert('Address copied to clipboard!')
            }
        }
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
        font-size: 9vh;
        text-align: right;
    }

    h2 {
        font-size: 20vh;
        color: white;
        text-shadow: 1px 1px 2px black
    }

    p.how-to {
        cursor: pointer;
        color: white;
        text-shadow: 1px 1px 2px black;
    }
</style>
