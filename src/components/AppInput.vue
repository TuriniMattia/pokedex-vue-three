<template>
    <input type="text" v-model="poke_name" placeholder="Cerca un pokemon" @keyup.enter="getPokemonByname">
    <button @click="getPokemonByname">CERCA</button>
</template>

<script>
import axios from 'axios';
import { store } from '/src/store.js';

export default {
    data() {


        return {
            store: store,
            poke_name: '',
        }
    },
    methods: {
        getPokemonByname() {
            axios.get(`https://pokeapi.co/api/v2/pokemon/${this.poke_name}`).then((res) => {
                console.log(res.data)
                this.store.pokemon = res.data


            })

        },
    },
}
</script>

<style lang="scss" scoped></style>