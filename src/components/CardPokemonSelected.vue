<script setup>
const pokemon = defineProps(["name", "exp", "weight", "height", "img"])


</script>

<template>
    <div class="card cardListPokemon">
        <img :src="pokemon.img" class="card-img-top pt-2" height="250" :alt="pokemon.name">
        <div class="card-body">
            <h5 class="card-title text-center">{{ pokemon.name }}</h5>
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
    height: 450px;
    background: rgb(63, 174, 251);
    background: radial-gradient(circle, rgba(63, 174, 251, 0.5211659663865546) 0%, rgba(70, 252, 186, 0.4651435574229692) 100%);
}
</style>