<template>
  <nuxt-link :to="'jokes/'+id">
    <div class="joke">
      <p class="joke-color">{{ joke }}</p>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Joke",
  props: {
    joke: String,
    id: String
  }
}
</script>

<style scoped>
  .joke {
    padding: 1rem;
    border: 1px dotted #ccc;
    margin: 1rem 0;
  }
  p:hover {
    color: #41b883
  }
</style>