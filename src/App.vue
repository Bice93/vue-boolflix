<template>
  <div id="app">
    <Header :searchFilm="searchFilm" @selectedFilm="updateSearchFilm(searchInput)"/>
    <Main :films="films" />
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
      apiUrl : 'https://api.themoviedb.org/3/search/movie?api_key=d2c0643db92db08a509446619d6878b8&query=',
    }
  },

  methods:{
    //CHIAMATA ALL'API ATTRAVERSO AXIOS
  getFilms: function(){
    axios.get(this.apiUrl+'searchInput')
    .then((result) => {
      console.log(result.data.results);
      this.films = result.data.results;
    })
    .catch((error) => {
      console.warn(error);
    })
  },
  },

  //APPENA CREO L'APPLICAZIONE CHIAMO LA FUNZIONE
  created(){
    this.getFilms();
  },

}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
