<template>
    <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-screen h-screen z-20 bg-white flex justify-center items-center" v-if="!pokemon">
        <div class="border-8 border-t-blue-700 w-20 h-20 rounded-full animate-spin">
            
        </div>
    </div>
    <div v-else class="text-center">
        <h1 class="text-5xl">Quien es este pokemon?</h1>
        <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon"/>
        <PokemonOptions @selection="checkAnswer" :options="pokemonArr"/>

        <template v-if="showAnswer">
            <h2 class="text-2xl my-8">{{message}}</h2>
            <button @click="resetGame" class="px-5 py-3 text-white bg-purple-600 rounded-md text-lg font-bold transition-all hover:-translate-y-0.5">Nuevo juego</button>
        </template>
    </div>
</template>

<script>
import PokemonOptions from '../components/PokemonOptions.vue'
import PokemonPicture from '../components/PokemonPicture.vue'

import {getPokemonOptions} from '@/helpers/getPokemonOptions'

export default {
    name: 'PokemonPage',
    data() {
        return {
            pokemonArr: [],
            pokemon: null,
            showPokemon: false,
            showAnswer: false,
            message: ''
        }
    },
    methods: {
        async mixPokemonArray(){
            this.pokemonArr = await getPokemonOptions();
            const randomPokemon = Math.floor(Math.random()*4);

            setTimeout(() => {
                this.pokemon = this.pokemonArr[randomPokemon]
            }, 500);
        },
        checkAnswer(id){
            this.showPokemon = true

            if(this.pokemon.id === id){
                this.message =`Excelente!!!`;
            }else{
                this.message =`Opsss, el pokemon es ${this.pokemon.name}`;
            }
            
            this.showAnswer = true

        },
        resetGame(){
            this.showPokemon = null;
            this.showAnswer = false;
            this.message = '';
            this.pokemon = null;
            this.pokemonArr = [];

            this.mixPokemonArray();
        }
    },
    mounted() {
        this.mixPokemonArray();
    },
    components: {
        PokemonOptions,
        PokemonPicture,
    }
}
</script>