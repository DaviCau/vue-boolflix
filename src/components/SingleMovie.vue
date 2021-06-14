<template>
    <section>
        <ol>
            <li>Titolo: {{item.title}}</li>
            <li>Titolo Originale: {{item.original_title}}</li>
            <li v-if="item.original_language == 'en'"><img src="../assets/images/en.png" alt="en"></li>
            <li v-else-if="item.original_language == 'it'"><img src="../assets/images/it.png" alt="it"></li>
            <li v-else>Lingua: {{item.original_language}}</li>
            <li>Voto: {{item.vote_average}}</li>
        </ol>
    </section>
</template>

<script>
export default {
    name: "SingleMovie",
    props: {
        "item": Object
    }
}
</script>

<style>
    img {
        height: 15px;
    }
</style>