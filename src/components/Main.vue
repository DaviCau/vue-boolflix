<template>
    <main>
        <SingleMovie v-for="(movie, index) in filteredMovie" :key="index" :item=movie />
    </main>
</template>

<script>
import SingleMovie from "./SingleMovie.vue"

export default {
    name: "Main",
    components: {
        SingleMovie
    },
    props: {
        "filteredMovie": Array
    }
}
</script>

<style>

</style>