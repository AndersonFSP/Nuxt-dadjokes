<template>
  <div>
    <nuxt-link to="/jokes">Back to jokes</nuxt-link>
    <h2>{{this.joke}} </h2>
    <hr>
    <small>Joke ID:  {{joke_id}}</small>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data(vm) {
    console.log()
    return {
      joke_id: vm.$route.params.id,
      joke: {}

    }
  },  
  computed: {
    baseUrl() {
      return this.$axios.defaults.baseURL;
    }
  },
  async created() {
    const config = {
      headers: {
        'Accept': 'application/json', 
      }
    }
    try {
      const res = await axios.get(`${this.baseUrl}j/${this.joke_id}`, config);
      this.joke = res.data.joke;
      console.log(this.joke);
    }catch(err) {
      console.log(err);
    }
  },

  
}
</script>

<style>

</style>