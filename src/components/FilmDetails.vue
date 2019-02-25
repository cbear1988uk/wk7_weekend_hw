<template lang="html">
  <div v-if="film">
    <h1>{{film.title}} ({{film.release_date}})</h1>
      <p>{{film.description}}</p>
      <p>Directed by: {{film.director}}</p>
      <p>Produced by: {{film.producer}}</p>
      <p>Rotten Tomatoes Score: {{film.rt_score}}</p>
  </div>
</template>

<script>
export default {
  name: 'film-details',
  props: ['film'],
}
</script>

<style lang="css" scoped>

div {
  margin-left: 200px;
  margin-right: 200px;
}

</style>
