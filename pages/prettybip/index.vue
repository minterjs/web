<template>
    <div class='container'>
        <h1>Генератор красивых адресов Minter</h1>
        <label for="filter">Фильтр</label>
      <input id="filter" v-model="filter"/>
        <button v-on:click="run">{{this.enabled && 'Остановить' || 'Начать'}}</button>
      <label for="end">Окончание</label>
      <input id="end" type="checkbox" model="inTheEnd"/>
        <p>Перебрано: {{attempts}}</p>
        <p>{{current.address}}</p>
        <p>{{current.mnemonic}}</p>
      <p><b>PRIVACY POLICY:</b><br/> Все вычисления производятся на стороне клиента без взаимодействия с сервером.</p>
      <p><b>ПОДДЕРЖАТЬ ПРОЕКТ:</b><br/>
        В целях повышенной безопасности сервис предоставляется <b>бесплатно</b>, но если он был Вам полезен - отправьте
        <b>10 PRETTYBIP</b> или любую другую сумму на адрес: <b>Mx00707ee371f0fdd7063de27b9117c42bc47c0abf</b></p>
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
            filter: 'Mx00',
            address: '',
            attempts: 0,
            enabled: false,
            current: {},
            ms: 0,
            inTheEnd: false,
        }},
        methods: {
            run() {
                this.enabled = !this.enabled;
                this.attempts = 0;
            },
            count() {
                this.ms = new Date('07-07-2019').getTime() - new Date().getTime();
            },
        },
        mounted() {

            setInterval(() => {
                let attempts = this.attempts;
                let c = this.current;
                let inTheEnd = this.inTheEnd;
                for (let i = 0; i < 30; i++){
                        if(this.enabled){
			    attempts++;
                            const wallet = generateWallet();
                            c = {
                                    address: wallet.getAddressString(),
                                    mnemonic: wallet.getMnemonic(),
                            };
                            if (inTheEnd && ((c.address + ' ').split(this.filter + ' ').length > 1) || (c.address.split(this.filter).length > 1)) {
                                this.enabled = false;
                            }
                        }
                }
                this.attempts = attempts;
                this.current = c;
                this.count();
            }, 1);
        }
}
</script>
