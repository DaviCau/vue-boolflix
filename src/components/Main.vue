<template>
    <main>
        <div class="container" v-if="filteredMovie.length > 0">
            <h3>Film</h3>
            <Card v-for="(movie, index) in filteredMovie" :key="index" :item=movie />
        </div>
        <div class="container" v-if="filteredSerie.length > 0">
            <h3>Serie Tv</h3>
            <Card v-for="(serie, index) in filteredSerie" :key="index" :item=serie />
        </div>
        <h2 v-if="filteredSerie.length == 0 && filteredMovie.length == 0 && isSearching">La ricerca non ha prodotto nessun risultato</h2>
    </main>
</template>

<script>
import Card from "./Card.vue"

export default {
    name: "Main",
    components: {
        Card
    },
    props: {
        "filteredMovie": Array,
        "filteredSerie": Array,
        "isSearching": Boolean
    }
}
</script>

<style lang="scss" scoped>

</style>