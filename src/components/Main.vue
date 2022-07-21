<template>
  <main>
    <div class="container">
      <h1>Main</h1>
      <CardElement v-for="film in films" 
      :key="film.id"
      :film="film"
       />
    </div>
    
  </main>
</template>

<script>
import CardElement from './CardElement.vue';

export default {
  props: {
    'films': {
        required: true,
        type: Array,
    }
  },
   components: {
    CardElement,
  }

}
</script>

<style>

</style>