<template lang="html">

  <div class="">
    <select v-on:change="handleChange">
      <option disable value=''>Select a film...</option>
      <option v-for="(film, index) in films" :key="index" :value="index">{{film.title}}</option>
    </select>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'films-list',
  props: ['films'],
  methods: {
    handleChange(){
      eventBus.$emit('clicked-film', this.films[event.target.value])
    }
  }
}
</script>

<style lang="css" scoped>

  div {
    padding: 50px;
  }

</style>
