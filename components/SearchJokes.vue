<template>
  <form @submit.prevent="onSubmit" >
    <input 
      type="text" 
      v-model="text" 
      placeholder="Search Jokes"
    />
    <input type="submit" value="Search">
  </form>
</template>

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      text: ''
    }
  },
  methods: {
    onSubmit() {
      this.$emit('search-text', this.text);
      this.text = "";
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  input[type=submit]  {
    background-color: #4CAF50;
    color: white;
    padding: 6px 9px;
    margin: 8px 0;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  input[type=text], select {

    padding: 5px 8px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
}
</style>

