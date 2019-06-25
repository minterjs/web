<template>
    <div class="landing">
        <div class="rotate">please rotate your device</div>
        <div class="container">
            <div>
                <logo/>
                <h1 class="title">
                    MINTERJS
                </h1>
                <h2 class="subtitle">
                    Work in progress
                </h2>
                <div class="links">
                    <a
                            href="#qr"
                            class="button--green"
                    >QR Code</a>
                    <a
                            href="#mazda6"
                            class="button--green"
                    >MAZDA6PLS</a>
                    <a
                            href="/mintercat"
                            class="button--green"
                    >MINTERCAT</a>
                    <a
                            href="https://github.com/minterjs"
                            class="button--grey"
                    >GitHub</a>
                    <a
                            href="http://teleg.run/MinterJSFeed"
                            class="button--grey"
                    >Telegram</a>
                </div>
            </div>
        </div>
        <a name="qr"/>
        <div class="container">
            <q-r-code-component></q-r-code-component>
        </div>
        <a name="mazda6"/>
        <div class="container">
            <mazda6></mazda6>
        </div>
    </div>
</template>

<script>
    import Logo from '~/components/Logo.vue'
    import QRCodeComponent from '~/components/QRCodeComponent.vue'
    import mazda6 from '~/components/mazda6.vue';

    export default {
        head: {
            title: 'minterjs.org',
        },
        components: {
            Logo,
            QRCodeComponent,
            mazda6,
        }
    }
</script>

<style>
    .container {
        margin: 0 auto;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
    }

    .title {
        font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
        'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
        display: block;
        font-weight: 300;
        font-size: 100px;
        color: #35495e;
        letter-spacing: 1px;
    }

    .subtitle {
        font-weight: 300;
        font-size: 42px;
        color: #526488;
        word-spacing: 5px;
        padding-bottom: 15px;
    }

    .links {
        padding-top: 15px;
    }
    .rotate {
        display: none;
    }
    @media all and (orientation:portrait) {
        .rotate {
            display: block;
            font-size: 30px;
            width: 100%;
            text-align: center;
        }
    }
</style>
