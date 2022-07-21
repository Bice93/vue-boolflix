<template>
  <header>
    <div class="container">
      <nav class="navbar bg-light">
          <form class="d-flex" role="search">
            <input
              class="form-control me-2"
              type="search"
              placeholder="Search"
              aria-label="Search"
              v-model="searchInput"
              @keyup.enter="(updateSearchFilm(searchInput))"
            />
            <button class="btn btn-outline-success" type="submit" @click.prevent=''>
              Search
            </button>
          </form>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  props: [
    'searchFilm'
  ],

  data: function(){
    return{
      searchInput:'',
    }
  },

  methods: {
    log(string){
      console.log(string);
    },
  },

  updateSearchFilm(search){
       this.$emit('selectedFilm', search);
  },

};
</script>

<style>
</style>