<template>
  <main>
    <div class="container">
      
        <h1 class="my-4">Film</h1>
        <section class="box_cards d-flex flex-wrap mt-3">
          <CardElement v-for="film in films" 
          :key="film.id" 
          :film="film" />
        </section>
      
      
        <h1 class="my-4">Serie Tv</h1>
        <section class="box_cards d-flex flex-wrap mt-3">
            <CardElementMovie
            v-for="movie in series"
            :key="movie.id"
            :movie="movie"
            />
        </section>
      
    </div>
  </main>
</template>

<script>
import CardElement from "./CardElement.vue";
import CardElementMovie from "./CardElementMovie.vue";

export default {
  props: {
    films: {
      required: true,
      type: Array,
    },

    series: {
      required: true,
      type: Array,
    },
  },
  components: {
    CardElement,
    CardElementMovie,
  },
};
</script>

<style lang="scss">
main {
  height: calc(100vh - 62px);
  background-color: rgb(105, 105, 105);
  overflow: scroll;
}

</style>