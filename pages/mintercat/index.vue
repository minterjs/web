<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-12">
                    <h1 class="title">Котики (всего {{cats.count}})</h1>
                    <p class="subtitle" v-on:click="copy">Экспериментальная версия, подкиньте MINTERCAT на развитие:
                        Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37</p>
                </div>
                <div class="col-md-8">
                    <form v-bind:action="'/mintercat/addr/' + search_addr" v-on:submit="search">
                        <input v-model="search_addr"/>
                        <button v-on:submit="search">Поиск</button>
                    </form>
                </div>
                <div class="col-md-4">
                    <script src="https://yastatic.net/es5-shims/0.0.2/es5-shims.min.js"></script>
                    <script src="https://yastatic.net/share2/share.js"></script>
                    <div class="ya-share2"
                         data-services="collections,vkontakte,facebook,odnoklassniki,moimir,twitter,telegram"></div>
                </div>
                <div class="col-md-3" v-for="cat in cats.cats">
                    <img class="img-thumbnail" v-bind:src="'http://mintercat.ml/img/Cat' + cat.img +'.png'"/>
                    <h2>{{cat.name}}</h2>
                    <p>Мин. цена: {{cat.price}} MINTERCAT</p>
                    <p>Вероятность: {{cat.rarity * 100}}%</p>
                </div>
                <div class="col-md-3">
                    <img src="/my.gif" class="img-thumbnail qr"/>
                    <h2>На котиков</h2>
                    <p>На полезные дела, на пиво, на ДР (07.07) и прочее)</p>
                </div>
                <div class="col-md-12">
                    <a href="//www.liveinternet.ru/click" target="_blank">
                        <img src="//counter.yadro.ru/hit?t50.15;r" alt="" title="LiveInternet" border="0" width="31"
                             height="31"/>
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'
    import copy from 'copy-to-clipboard';

    export default {
        name: "index.vue",
        head: {
            title: 'Minter котики | MINTERCAT'
        },
        async asyncData() {
            return {
                cats: await axios.get('http://mintercat.ml/api/').then(res => res.data),
            }
        },
        data() {
            return {
                search_addr: 'Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37',
            }
        },
        methods: {
            copy() {
                copy('Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37');
                alert('Адрес скорирован, MINTERCAT accepted here ;-)')
            },
            async search() {
                document.location.href = '/mintercat/addr/' + this.search_addr;
            }
        },
    }
</script>

<style scoped>
    .title, .subtitle {
        text-align: center;
    }

    .subtitle {
        cursor: pointer;
    }

    input {
        min-width: 50%;
    }

    .qr {
        min-width: 100%;
    }
</style>
