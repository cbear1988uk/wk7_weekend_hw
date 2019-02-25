<template lang="html">
  <div id="app">
    <h1>株式会社スタジオジブリ</h1>
    <h2>Studio Ghibli</h2>
    <iframe width="840" height="472" src="https://www.youtube.com/embed/v6Q6y4-qKac?controls=0&autoplay=1" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
      <div class="main-container">
        <p>Search</p>
        <search-box :films='films'></search-box>
        <films-list :films='films'></films-list>
        <film-details :film="selectedFilm" :characters="characters"></film-details>
      </div>
      <footer>copyright Studio Ghibli Inc.©</footer>
  </div>
</template>

<script>
import FilmsList from './components/FilmsList.vue';
import FilmDetails from './components/FilmDetails.vue';
import SearchBox from './components/SearchBox.vue';

import {eventBus} from './main.js';


export default {
  data(){
    return{
      films: [],
      selectedFilm: null,
      characters: []
    }
  },
  components: {
    "films-list": FilmsList,
    "film-details": FilmDetails,
    "search-box": SearchBox
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(films => this.films = films)

    fetch('https://ghibliapi.herokuapp.com/people/')
    .then(res => res.json())
    .then(characters => this.characters = characters)
    eventBus.$on('clicked-film', (film) =>{
      this.selectedFilm = film
    })
  }
}
</script>

<style lang="css" scoped>
* {
  font-family: 'Montserrat', sans-serif;
  text-align: center;
  color: red;
  background-color: black;
  background-size: auto;

}

body {
  margin: 0;
}

p {
  margin-bottom: 0px;
}

h1 {
  text-decoration: underline;
  margin-bottom: 0px;
}

h2 {
  font-size: 50px;
  margin-top: 0px;
  margin-bottom: 10px;
}

footer {
  padding: 20px;
  padding-top: 300px;
}

</style>
