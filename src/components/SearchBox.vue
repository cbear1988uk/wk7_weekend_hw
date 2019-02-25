<template lang="html">
  <div>
    <input type="text" v-model="searchInput" v-on:input="search">
      <div v-if="filteredFilms.length > 0">
        <film-details v-for="(film, index) in filteredFilms" :film="film" :key="index"></film-details>
      </div>
  </div>
</template>

<script>
import FilmDetails from './FilmDetails.vue'

export default {
  data(){
    return {
      searchInput: '',
      filteredFilms: []
    }
  },
  name: 'search-box',
  props: ['films'],
  components: {
    "film-details": FilmDetails
  },
  methods: {
    search(){
      const filteredFilms = this.films.filter(film => film.title.toLowerCase().includes(this.searchInput.toLowerCase()))
      this.filteredFilms = filteredFilms
    }
  }
}
</script>

<style lang="css" scoped>

input {
  color: red;
  height: 20px;
  width: 200px;
  margin: 20px;
  font-size: 20px;
}

</style>
