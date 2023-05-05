<script setup>
const pokemon = defineProps(["name", "exp", "weight", "height", "img", "loading"])


</script>

<template>
    <div class="card cardListPokemon" :class="loading ? '' : 'animate__animated animate__flipInY'">
        <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top pt-2" height="250" :alt="pokemon.name">
        <img v-else src="../assets/egg-pokemon-incubator.svg" class="card-img-top pt-2" height="250" alt="???">
        <div class="card-body">
            <h5 class="card-title text-center">{{ pokemon.name || '???' }}</h5>
            <hr>
            <div class="row">
                <section class="col">
                    <strong>exp: </strong>
                    <span>{{ pokemon.exp }}</span>
                </section>
                <section class="col">
                    <strong>peso: </strong>
                    <span>{{ pokemon.weight }}</span>
                </section>
                <section class="col">
                    <strong>altura: </strong>
                    <span>{{ pokemon.height }}</span>
                </section>
            </div>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
                content.</p>
        </div>
    </div>
</template>

<style scoped>
.cardListPokemon {
    height: 75vh;
    background: rgb(63, 174, 251);
    background: radial-gradient(circle, rgba(63, 174, 251, 0.5211659663865546) 0%, rgba(70, 252, 186, 0.4651435574229692) 100%);
}
</style>