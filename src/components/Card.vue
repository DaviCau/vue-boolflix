<template>
    <section>
        <div class="poster" @mouseleave="mouseOver" @mouseenter="mouseOver">
            <img v-if="item.poster_path != null" :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" :alt="`${item.title ? item.title : item.name}`">
            <img v-else src="https://www.altavod.com/assets/images/poster-placeholder.png" :alt="`${item.title ? item.title : item.name}`">

            <ul v-if="active">
                <li><strong>Titolo:</strong> {{item.title ? item.title : item.name}}</li>
                <li><strong>Titolo originale:</strong> {{item.original_title ? item.original_title : item.original_name}}</li>
                <li>
                    <img class="flag-img" :src="require(`../assets/images/${item.original_language}.png`)" :alt="`bandiera ${item.original_language}`" v-if="aviableFlags.includes(item.original_language)">
                    <span v-else><strong>Lingua originale:</strong> {{item.original_language}}</span>
                </li>
                <li>
                    <strong>Voto:</strong> <i v-for="n in 5" :key="n" class="fa-star star" :class="(n <= getVote()) ? 'fas' : 'far'"></i>
                </li>
                <li v-if="item.overview.length > 0">
                    <strong>Overview:</strong> {{getOverview()}}
                </li>
            </ul>
        </div>
    </section>
</template>

<script>
export default {
    name: "Card",
    data: function() {
        return {
            aviableFlags: ["en", "it"],
            active: false
        }
    },
    methods: {
        getVote: function() {
            return Math.ceil(this.item.vote_average / 2)
        },
        getOverview: function() {
            if (this.item.overview.length > 700) {
                return `${this.item.overview.slice(0, 700)}...`
            }
            return this.item.overview
        },
        mouseOver: function(){
            this.active = !this.active;   
        }
    },
    props: {
        "item": Object
    }
}
</script>

<style lang="scss" scoped>
    section {
        margin: 0 5px 30px;

        .poster {
            position: relative;
            width: 342px;
            background-color: black;
            display: flex;

            &:hover > img {
                opacity: 0.1;
            }

            & > img {
                width: 342px;
                height: 515px;
            }

            ul {
                list-style: none;
                position: absolute;
                top: 0;
                left: 0;
                padding: 20px;
                color: white;

                li {
                    padding-bottom: 10px;
                }

                .flag-img {
                    width: 40px;
                }

                .star {
                    color: gold;
                }
            }
        }
    }
</style>