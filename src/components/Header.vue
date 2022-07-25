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
              @keyup.enter="$emit('selected-film', searchInput), 
              $emit('selected-series', searchInput)"
            />
            
            <button class="btn btn-outline-success" type="submit" 
            @click.prevent="$emit('selected-film', searchInput),
             $emit('selected-series', searchInput)">
              Search
            </button>
          </form>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data: function(){
    return{
      searchInput:'',
    }
  },

  methods: {
    // log(string){
    //   console.log(string);
    // },
  },
};
</script>

<style>
</style>