<template>
  <div>
    <img :src="takeImg(movie)" :alt="movie.title" />
    <ul>
      <li>{{ movie.name }}</li>
      <li>{{ movie.original_name }}</li>
      <li>
        Lingua originale:
        <img
          v-if="languages.includes(movie.original_language)"
          :src="require(`../assets/img/${movie.original_language}.png`)"
          :alt="`../assets/img/${movie.original_language}.png`"
        />
        <span v-else> {{ movie.original_language }} </span>
      </li>

      <li>
        Voto:
        <i v-for="n in 5" :key="n" class="far fa-star"></i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: [
    "movie"
    ],

  data: function () {
    return {
      languages: ["en", "it"],
    };
  },

  methods: {
    //FUNZIONE PER PRELEVARE L'IMMAGINE DELLA CARD
    takeImg(element) {
      if (element.poster_path != null) {
        return "https://image.tmdb.org/t/p/w342" + element.poster_path;
      }
    },
    //FUNZIONE PER I VOTI
    takeVotes(element) {
      return Math.ceil(element / 2);
    },
  },
};
</script>

<style lang="scss">
</style>