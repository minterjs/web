<template>
    <div class='container'>
        <h1>Генератор красивых адресов Minter</h1>
        <label for="filter">Фильтр</label>
        <input name="filter" v-model="filter" />
        <button v-on:click="run">{{this.enabled && 'Остановить' || 'Начать'}}</button>
        <p>Перебрано: {{attempts}}</p>
        <p>{{current.address}}</p>
        <p>{{current.mnemonic}}</p>
        <p>Донейт на развитие: Mx00707ee371f0fdd7063de27b9117c42bc47c0abf/p>
    </div>
</template>

<script>
import {generateWallet} from 'minterjs-wallet';
import { setTimeout, setInterval } from 'timers';
export default {
        name: "index.vue",
        head: {
            title: "PRETTYBIP"
        },
        data() {return {
            filter: 'Mx007',
            address: '',
            attempts: 0,
            enabled: false,
            current: {},
        }},
        methods: {
            run() {
                this.enabled = !this.enabled;
                this.attempts = 0;
            }
        },
        mounted() {
            setInterval(() => {
                        if(this.enabled){
                            this.attempts++;
                            const wallet = generateWallet();
                            const c = {
                                    address: wallet.getAddressString(),
                                    mnemonic: wallet.getMnemonic(),
                            };
                            this.current = c;
                            if(c.address.split(this.filter). length > 1){
                                this.enabled = false;
                            }
                        }
            }, 1);
        }
}
</script>
