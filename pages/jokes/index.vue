<template>
  <div >
    <SearchJokes @search-text="searchText"/>
    <Joke 
      v-for="joke in jokes" 
      :key="joke.id"
      :id="joke.id"
      :joke="joke.joke" 
    />
    <div v-if="!jokes.length">
      <h2 style="margin-top:15px;">No joke was found :(</h2> 
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Joke from '../../components/Joke';
import SearchJokes from '../../components/SearchJokes';

export default {
  components: {
    Joke,
    SearchJokes
  },
  data() {
    return {
      jokes: []
    }
  },

  computed: {
    baseUrl() {
      return this.$axios.defaults.baseURL;
    },
    config() {
      return { 
        headers: {
        'Accept': 'application/json', 
       }
      }
    }
  },

  methods: {
    async searchText(text) {
      try {
        const res = await axios.get(`${this.baseUrl}search?term=${text}`, this.config);
        this.jokes = res.data.results;
      }catch(err) {
      console.log(err);
      }
    }
  },

  async created() {
    try {
      const res = await axios.get(`${this.baseUrl}search`, this.config);
      this.jokes = res.data.results;
      
    }catch(err) {
      console.log(err);
    }
  },
  head() {
    return {
      title: "Dad Jokes",
      meta: [
        {
          hid: 'description',
          name: "description",
          content: "Best Place for dad jokes"
        }
      ]
    }
  }
}
</script>

<style>

</style>