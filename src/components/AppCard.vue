<template>
    <div class="poke_sprite">

        <img class="poke_sprite_img" :src="getSprite" alt="" @click="pokeCries">
        <font-awesome-icon @click="prevSlide" class="icona_1" :icon="['far', 'circle-left']" />
        <font-awesome-icon @click="nextSlide" class="icona_2" :icon="['far', 'circle-right']" />
    </div>
    <div class="poke-name">
        {{ pokemonData ? pokemonData.name : 'Cerca un Pokemon' }}

    </div>

</template>

<script>
import { toRaw } from 'vue';
import { store } from '../store.js'
export default {
    props: {
        pokemonData: Object
    },
    data() {


        return {
            spriteIndex: 0,
        }
    },
    watch: {
        pokemonData: function (newVal, oldVal) {
            const v = toRaw(newVal);
            this.spriteIndex = this.getFirstImageIndex(v.sprites)
        }
    },
    computed: {
        getSprite() {
            console.log('here', this.pokemonData)
            if (this.pokemonData && this.pokemonData.sprites) {
                const avaibleSprites = this.getAvaibleSprites()
                const keys = Object.keys(avaibleSprites)
                console.log('keys', keys)
                const currentKey = keys[this.spriteIndex];
                const currentSprite = avaibleSprites[currentKey]

                return currentSprite
            } else {
                return '/what-does-this-mean-v0-hyx2v97q0whb1.webp'
            }

        },


    },
    methods: {
        getAvaibleSprites() {
            const result = Object.entries(this.pokemonData.sprites).filter(([key, value]) => value !== null && key !== 'other' && key !== 'versions');
            return Object.fromEntries(result);
        },

        nextSlide() {
            const keys = Object.keys(this.getAvaibleSprites())
            console.log(keys)
            if (this.spriteIndex < keys.length - 1) {
                this.spriteIndex++
            } else {
                this.spriteIndex = 0
            }

        },
        prevSlide() {
            const keys = Object.keys(this.getAvaibleSprites())
            if (this.spriteIndex === 0) {
                this.spriteIndex = keys.length - 1
            } else {
                this.spriteIndex--
            }
        },
        getFirstImageIndex(data) {
            const index = Object.entries(data)
                .filter(([key, value]) => value !== null && key !== 'other' && key !== 'versions')
                .findIndex(([key, value]) => key === 'front_default')
            console.log(index)
            return index
        },
        pokeCries() {
            const audio = new Audio(this.pokemonData.cries.latest)
            audio.volume = 0.2
            audio.play()

        }
    },
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
    // position: relative;
}

.icona_1 {
    position: absolute;
    top: 25%;
    left: 30%;
    font-size: 40px;
    cursor: pointer;
}

.icona_2 {
    position: absolute;
    top: 25%;
    right: 30%;
    font-size: 40px;
    cursor: pointer;
}
</style>