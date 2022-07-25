<template>
  <header class="p-1">
    <div class="container d-flex justify-content-between align-items-center">
        <!-- Logo -->
        <div class="logo_header">
          <h2>Boolflix</h2>
        </div>
        <!-- Input search -->
        <nav class="navbar ms_navbar">
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

              <button class="btn btn-light" type="submit" 
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

<style lang="scss" scoped>
header{
  background-color: black;
    
    .ms_navbar{
      background-color: black;
    };

    // Stile Logo
    h2{
      text-transform: uppercase;
      color: red;
    };
}
</style>