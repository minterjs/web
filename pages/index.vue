<template>
    <div class="landing">
        <div class="rotate">please rotate your device</div>
        <div class="container-x">
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
                    <br />
                    <br />
                    <a href="/prettybip"class="button--green">Создать красивый адрес Minter</a>
                </div>
            </div>
        </div>
        <a name="qr"/>
        <div class="container-x">
            <q-r-code-component></q-r-code-component>
        </div>
        <div class="container-x">
            <h2 class='subtitle'>До моей 30ки осталось: {{ms}}</h2>
        </div>
        <a name="mazda6"/>
        <div class="container-x">
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
        },
        methods: {
            count() {
                this.ms = new Date('07-07-2019').getTime() - new Date().getTime();
            },
        },
        mounted() {
            setInterval(() => {this.count()}, 1);
        },
        data(){
            return {
                ms: 0,
            };
        }
    }
</script>

<style>
    .container-x {
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
