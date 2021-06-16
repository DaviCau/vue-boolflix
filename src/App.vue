<template>
  <div id="app">
    <Header @moviesFound="moviesFound" @seriesFound="seriesFound" />
    <Main :filteredMovie="moviesToShow" :filteredSerie="seriesToShow" :isSearching="searchStarted" />
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data: function() {
    return {
      moviesToShow: [],
      seriesToShow: [],
      searchStarted: false
    }
  },
  methods: {
    moviesFound: function(array) {
      this.moviesToShow = array;
      this.searchStarted = true;
    },
    seriesFound: function(array) {
      this.seriesToShow = array
    }
  }
}
</script>

<style lang="scss">
  
</style>
