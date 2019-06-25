<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-12">
                    <h1 class="title" v-on:click="pp">Котики (всего {{cats.count}})</h1>
                    <p class="subtitle" v-on:click="copy">Экспериментальная версия, подкиньте MINTERCAT на развитие:
                        Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37</p>
                </div>
                <div class="col-md-3" v-for="cat in cats.cats">
                    <img class="img-thumbnail" v-bind:src="'http://mintercat.ml/img/Cat' + cat.img +'.png'"/>
                    <h2>{{cat.name}}</h2>
                    <p>Мин. цена: {{cat.price}} MINTERCAT</p>
                    <p>Вероятность: {{cat.rarity * 100}}%</p>
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

        methods: {
            copy() {
                copy('Mx7926f1944b8faabb3b440b394543ae6f5b2f8f37');
                alert('Адрес скорирован, MINTERCAT accepted here ;-)')
            }
        },

        created() {
            console.log(this.cats);
        }
    }
</script>

<style scoped>
    .title, .subtitle {
        text-align: center;
    }

    .subtitle {
        cursor: pointer;
    }
</style>
