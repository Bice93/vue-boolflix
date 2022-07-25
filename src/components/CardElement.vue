<template>
  <div class="ms_card m-3">
    <div class="flip_card">
      <div class="cover_image">
        <img v-if="takeImg(film)" :src="takeImg(film)" :alt="film.title" />
        <img v-else src="../assets/img/Noimage.png" :alt="film.title">
      </div>

      <div class="info_card py-5">
        <ul>
          <li><span class="fw-bold">Titolo: </span> {{ film.title }}</li>
          <li>
            <span class="fw-bold">Titolo Originale: </span>
            {{ film.original_title }}
          </li>

          <li>
            <span class="fw-bold">Lingua originale: </span>
            <img
              class="flag"
              v-if="languages.includes(film.original_language)"
              :src="require(`../assets/img/${film.original_language}.png`)"
              :alt="`../assets/img/${film.original_language}.png`"
            />
            <span v-else> {{ film.original_language }} </span>
          </li>

          <li>
            <span class="fw-bold">Voto: </span>
            <i
              v-for="n in 5"
              :key="n"
              class="fa-star ms_star"
              :class="n <= takeVotes(film.vote_average) ? 'fas' : 'far'"
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
    "film",
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
      // return '';
    },
    //FUNZIONE PER I VOTI
    takeVotes(element) {
      return Math.ceil(element / 2);
    },
  },
};
</script>

<style lang="scss">
.ms_card {
  width: 345px;
  height: 515px;
  text-align: center;
  position: relative;
  perspective: 1000px;
}

.flip_card {
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.ms_card:hover .flip_card {
  transform: rotateY(180deg);
}

.cover_image,
.info_card {
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.info_card {
  width: 100%;
  height: 100%;
  background-color: black;
  color: white;
  position: absolute;
  top: 0;
  left: 0;
  transform: rotateY(180deg);

  ul {
    list-style: none;
  }
}

.cover_image img {
  width: 100%;
}

.flag {
  width: 20px;
}

.ms_star {
  color: gold;
}
</style>