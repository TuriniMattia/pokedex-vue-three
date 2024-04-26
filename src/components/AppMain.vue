<template>
    <main class="pokedex_page">

        <div class="card_container">
            <AppCard :pokemonData="this.store.pokemon" />
            <div class="input_pokemon_container">
                <AppInput />

            </div>



        </div>
    </main>

</template>

<script>
import AppCard from './AppCard.vue'
import AppInput from './AppInput.vue'
import { store } from '../store.js'
import axios from 'axios';

export default {
    components: {
        AppInput,
        AppCard,
    },
    data() {


        return {
            store: store,


        }
    },

}
</script>

<style lang="scss" scoped>
//MAIN//
.pokedex_page {
    display: flex;
    justify-content: center;
    align-items: center;
}

//CARD CONTAINER//
.card_container {
    width: 600px;
    height: 1000px;
    background-color: red;
    border: black 2px solid;
    display: flex;
    flex-direction: column;
    align-items: center;


}

//INPUT CONTAINER//

.input_pokemon_container {
    margin-top: 50px;
}
</style>