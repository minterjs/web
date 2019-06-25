<template>
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <h2 class="title">Котики на адресе {{addr}}</h2>
                <p class="subtitle" v-on:click="copy">Экспериментальная версия, подкиньте MINTERCAT на развитие:
                    Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37</p>
            </div>
            <div class="col-md-8">
                <form v-bind:action="'./' + search_addr" v-on:submit="search"><input v-model="search_addr"/>
                    <button v-on:submit="search">Поиск</button>
                </form>
            </div>
            <div class="col-md-4">
                <script src="https://yastatic.net/es5-shims/0.0.2/es5-shims.min.js"></script>
                <script src="https://yastatic.net/share2/share.js"></script>
                <div class="ya-share2"
                     data-services="collections,vkontakte,facebook,odnoklassniki,moimir,twitter,telegram"></div>
            </div>
            <div class="col-md-3" v-for="cat in cats">
                <img class="img-thumbnail" v-bind:src="'http://mintercat.ml/img/Cat' + cat.img +'.png'"/>
                <h2>{{cats_details.cats.find(catd => catd.img == cat.img).name}}</h2>
                <p>Мин. цена: {{cat.price}} MINTERCAT</p>
                <p>Вероятность: {{cat.rarity * 100}}%</p>
                <p>Id: {{cat.stored_id}}</p>
            </div>
            <div class="col-md-3">
                <img src="/my.gif" class="img-thumbnail qr">
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
</template>

<script>
    import axios from 'axios';
    import 'bootstrap/dist/css/bootstrap.css'
    import 'bootstrap-vue/dist/bootstrap-vue.css'
    import copy from 'copy-to-clipboard';

    export default {
        name: "Addr",
        head() {
            return {
                title: 'MINTERCAT Explorer: ' + this.addr + ' | Minter котики'
            }
        },
        async asyncData({params}) {
            return {
                addr: params.addr,
                search_addr: params.addr,
                cats_details: await axios.get('http://mintercat.ml/api/').then(res => res.data),
                cats_addr: await axios.get(`http://api.minterjs.org:7770/addr?addr=${params.addr}`).then(res => res.data),
            }
        },
        methods: {
            copy() {
                copy('Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37');
                alert('Адрес скорирован, MINTERCAT accepted here ;-)')
            },
        },
        computed: {
            cats() {
                return this.cats_addr.map(cat => {
                    const details = this.cats_details.cats.find(cd => cd.img == cat.img);
                    return {...cat, ...details};
                })
            }
        }
    }
</script>

<style scoped>
    .title, .subtitle {
        text-align: center;
    }

    input {
        min-width: 50%;
    }

    .qr {
        min-width: 100%;
    }
</style>
