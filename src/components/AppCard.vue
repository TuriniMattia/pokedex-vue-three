<template>
    <div class="poke_sprite">
        <img class="poke_sprite_img" :src="getSprite" alt="">
    </div>
    <div class="poke-name">
        {{ pokemonData ? pokemonData.name : 'Cerca un Pokemon' }}
    </div>

</template>

<script>
export default {

    props: {
        pokemonData: Object
    },
    data() {


        return {}
    },
    computed: {
        getSprite() {
            console.log('here', this.pokemonData)
            if (this.pokemonData && this.pokemonData.sprites) {

                return this.pokemonData.sprites.front_default
            } else {
                return '/public/what-does-this-mean-v0-hyx2v97q0whb1.webp'
            }


        }
    }
}
</script>

<style lang="scss" scoped>
//pokename//
.poke-name {

    font-size: 30px;
    font-weight: bold;
    text-transform: uppercase;
    margin-top: 100px;


}

.poke_sprite {
    width: 300px;
    height: 300px;
    background-color: white;
    margin-top: 100px;
}

.poke_sprite_img {
    width: 100%;
}
</style>