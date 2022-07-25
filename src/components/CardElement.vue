<template>
  <div>
    <img :src="takeImg(film)" :alt="film.title" />
    <ul>
      <li>{{ film.title }}</li>
      <li>{{ film.original_title }}</li>

      <li>
        Lingua originale:
        <img
          v-if="languages.includes(film.original_language)"
          :src="require(`../assets/img/${film.original_language}.png`)"
          :alt="`../assets/img/${film.original_language}.png`"
        />
        <span v-else> {{ film.original_language }} </span>
      </li>

      <li>
        Voto:
        <!-- {{ takeVotes(film.vote_average) }}  -->
        <i
          v-for="n in 5"
          :key="n"
          class="fa-star"
          :class="n <= takeVotes(film.vote_average) ? 'fas' : 'far'"
        ></i>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: [
    "film"
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

<style lang="scss" scoped>
</style>