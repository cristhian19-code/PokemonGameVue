<template>
<div class="pokemon-container my-9">
    <img class="block mx-auto hidden-pokemon" :src="imgSrc" alt="">
    <img v-if="showPokemon" class="block mx-auto fade-in" :src="imgSrc" alt="">
</div>
</template>

<script>
export default {
    props: {
        pokemonId: {
            type: Number,
            required: true,
            default: 1
        },
        showPokemon: {
            type: Boolean,
            required: true,
            default: false
        }
    },
    computed: {
        imgSrc(){
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokemonId}.svg`
        }
    }
}
</script>

<style scoped>
.pokemon-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 200px;
    position: relative;
}

img {
    height: 100%;
    top: 0;
    position: absolute;
    user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}

.hidden-pokemon {
    filter: brightness(0);
}
</style>