<template>
  <div id="app">
    <Header @movieFound="movieFound" />
    <Main :filteredMovie="movieToShow" />
  </div>
</template>

<script>
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
      movieToShow: []
    }
  },
  methods: {
    movieFound: function(array) {
      this.movieToShow = array
    }
  }
}
</script>

<style lang="scss">

</style>
