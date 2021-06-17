<template>
    <main>
        <div class="main-container">
            <h2 v-if="filteredMovie.length > 0">Film</h2>
            <div class="card-container" v-if="filteredMovie.length > 0">
                <Card v-for="(movie, index) in filteredMovie" :key="index" :item=movie />
            </div>
            <h2 v-if="filteredSerie.length > 0">Serie Tv</h2>
            <div class="card-container" v-if="filteredSerie.length > 0">
                <Card v-for="(serie, index) in filteredSerie" :key="index" :item=serie />
            </div>
            <h2 v-if="filteredSerie.length == 0 && filteredMovie.length == 0 && isSearching">La ricerca non ha prodotto nessun risultato</h2>
        </div>
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
    main {
        min-height: 100vh;
        padding: 100px 0 50px;
        background-color: #434343;

        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            

            h2 {
                margin: 20px 0;
                color: #dc1a28;
                font-size: 32px;
            }

            .card-container {
                display: flex;
                width: 95%;
                flex-wrap: wrap;
                justify-content: center;
                align-items: center;
            }
        }
    }
</style>