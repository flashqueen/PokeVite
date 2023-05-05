<script setup>
const pokemon = defineProps(["name", "urlBaseSvg"])
</script>

<template>
    <div class="col-4 col-md-6 col-xl-3">
        <div class="card p-2 mb-3 cardListPokemon   ">
            <p class="text-center">{{ pokemon.name }}</p>
            <img :src="urlBaseSvg" class="card-img-top" alt="..." height="80" />
        </div>
    </div>
</template>

<style scoped>
.cardListPokemon {
    background: rgb(63, 174, 251);
    background: radial-gradient(circle, rgba(63, 174, 251, 0.7211659663865546) 0%, rgba(70, 252, 186, 0.6651435574229692) 100%);
}

.cardListPokemon:hover {
    background: rgb(63, 174, 251);
    background: radial-gradient(circle, rgba(63, 174, 251, 0.9211659663865546) 0%, rgba(70, 252, 186, 0.8651435574229692) 100%);
    cursor: pointer;
}

.cardListPokemon img:hover {
    padding: .1rem;
}
</style>