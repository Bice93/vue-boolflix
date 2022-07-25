<template>
  <main>
    <div class="container">
      <h1>Main</h1>
      <CardElement v-for="film in films" 
      :key="film.id"
      :film="film"

       />
       <CardElementMovie v-for="movie in series"
        :key="movie.id" 
        :movie="movie" />
    </div>
    
  </main>
</template>

<script>
import CardElement from './CardElement.vue';
import CardElementMovie from './CardElementMovie.vue';

export default {
  props: {
    'films': {
        required: true,
        type: Array,
    },

    'series': {
        required: true,
        type: Array,
    },
  },
   components: {
    CardElement,
    CardElementMovie,
  }

}
</script>

<style>

</style>