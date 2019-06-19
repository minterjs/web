<template>
    <div class="qr-wrapper">
        <h2 class="title">Create QRCode<span class="or-donate"
                                             v-if="address == 'Mx00c743f4fdeccd5d98aca88f4c18b53f29af9645'"> or donate</span>
        </h2>
        <div class="address">
            <input v-model="address"/>
        </div>
        <div class="qrcode">
            <img v-bind:src="this.qrcode"/>
        </div>

    </div>
</template>

<script>
    import QRCode from 'qrcode';

    export default {
        name: "QRCodeComponent",
        data() {
            return {
                address: 'Mx00c743f4fdeccd5d98aca88f4c18b53f29af9645',
                qrcode: null,
            }
        },
        created() {
            QRCode.toDataURL(this.address).then(url => this.qrcode = url).catch(e => console.log(e.message));
        },
        watch: {
            address(val) {
                QRCode.toDataURL(val).then(url => this.qrcode = url).catch(e => console.log(e.message));
            }
        }
    }
</script>

<style scoped>
    .qr-wrapper {
        width: 100%;
        height: 100%;
        background: black;
        margin: 0 auto;
        min-height: 100vh;
        -webkit-justify-content: center;
        justify-content: center;
        -webkit-align-items: center;
        align-items: center;
        text-align: center;
    }

    input {
        padding: 1vh 1vw;
        font-size: 7vh;
    }

    h2, input, .qrcode {
        margin: 5vh 5vw;
    }

    h2.title {
        margin-top: 10vh;
        color: #fff;
    }

    .title {
        font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
        'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
        display: block;
        font-weight: 300;
        font-size: 10vh;
        color: #35495e;
        letter-spacing: 1px;
    }
</style>
