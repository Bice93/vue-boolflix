<template>
  <div class="ms_card m-3">
    <div class="flip_card">
      <div class="cover_image">
        <img v-if="takeImg(movie)" :src="takeImg(movie)" :alt="movie.name" />
        <img v-else src="../assets/img/Noimage.png" :alt="movie.title">
      </div>

      <div class="info_card py-5">
        <ul>
          <li><span class="fw-bold">Titolo: </span> {{ movie.name }}</li>
          <li>
            <span class="fw-bold">Titolo Originale: </span>
            {{ movie.original_movie }}
          </li>

          <li>
            <span class="fw-bold">Lingua originale: </span>
            <img
              class="flag"
              v-if="languages.includes(movie.original_language)"
              :src="require(`../assets/img/${movie.original_language}.png`)"
              :alt="`../assets/img/${movie.original_language}.png`"
            />
            <span v-else> {{ movie.original_language }} </span>
          </li>

          <li>
            <span class="fw-bold">Voto: </span>
            <i
              v-for="n in 5"
              :key="n"
              class="fa-star ms_star"
              :class="n <= takeVotes(movie.vote_average) ? 'fas' : 'far'"
            ></i>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    "movie",
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