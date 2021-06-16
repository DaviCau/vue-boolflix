<template>
    <section>
        <ul>
            <li>{{item.title ? item.title : item.name}}</li>
            <li>{{item.original_title ? item.original_title : item.original_name}}</li>
            <li>
                <img class="flag-img" :src="require(`../assets/images/${item.original_language}.png`)" :alt="`bandiera ${item.original_language}`" v-if="aviableFlags.includes(item.original_language)">
                <span v-else>{{item.original_language}}</span>
            </li>
            <li><span class="star" v-for="n in vote" :key="n"><i class="fas fa-star"></i></span></li>
            <li><img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" :alt="`${item.title}`"></li>
        </ul>
    </section>
</template>

<script>
export default {
    name: "Card",
    data: function() {
        return {
            aviableFlags: ["en", "it"],
            vote: Math.ceil(this.item.vote_average / 2)
        }
    },
    props: {
        "item": Object
    }
}
</script>

<style lang="scss" scoped>
    .flag-img {
        height: 15px;
    }

    .star {
        color: gold;
    }
</style>