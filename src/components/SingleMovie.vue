<template>
    <section>
        <ol>
            <li>Titolo: {{item.title}}</li>
            <li>Titolo Originale: {{item.original_title}}</li>
            <li>Lingua: {{item.original_language}}</li>
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

</style>