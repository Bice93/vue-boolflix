<template>
  <div id="app">
    <Header />
    <Main :films="films" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
//import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data: function() {
    return{
      films : [
        '1',
        '2',
        '3',
      ],

      apiUrl : '',
    }
  },

  // methods:{
  //   //CHIAMATA ALL'API ATTRAVERSO AXIOS
  // getFilms: function(){
  //   axios.get(this.apiUrl)
  //   .then((result) => {
  //     console.log(result);
  //     this.films = result;
  //   })
  //   .catch((error) => {
  //     console.warn(error);
  //   })
  // }
  // },

  // //APPENA CREO L'APPLICAZIONE CHIAMO LA FUNZIONE
  // created(){
  //   this.getFilms();
  // },

}
</script>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";

</style>
