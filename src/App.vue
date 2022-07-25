<template>
  <div id="app">
    <Header @selected-film="getFilms" @selected-series="getSeries"/>
    <Main :films="films" :series="series"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data: function() {
    return{
      films : [],
      series: [],
      apiUrlFilm : 'https://api.themoviedb.org/3/search/movie?api_key=d2c0643db92db08a509446619d6878b8&query=',
      apiUrlSeries: `https://api.themoviedb.org/3/search/tv?api_key=d2c0643db92db08a509446619d6878b8&query=`,
    }
  },

  methods:{
    //CHIAMATA ALL'API ATTRAVERSO AXIOS PER I FILMS
    getFilms: function(inputSearch){
        //console.log(inputSearch)
        axios.get(this.apiUrlFilm+inputSearch)
        .then((result) => {
          console.log(result.data.results);
          this.films = result.data.results;
        })
        .catch((error) => {
          console.warn(error);
        })
    },

    //CHIAMATA ALL'API ATTRAVERSO AXIOS PER I FILMS
    getSeries: function(inputSearch){
        //console.log(inputSearch)
        axios.get(this.apiUrlSeries+inputSearch)
        .then((result) => {
          console.log(result.data.results);
          this.series = result.data.results; 
        })
        .catch((error) => {
          console.warn(error);
        })
    },
  },

}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
