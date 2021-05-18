<!-- jokes index -->
<template>
  <div>
    <Search @search-text='searchText' />
    <ul class="uk-list uk-list-striped uk-list-large">
      <li v-for='(joke, index) in jokes' :key='joke.id'>
        <Joke :id='joke.id' :joke='joke.joke' :index="index + 1" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  head() {
    return {
      title: "Jokes",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Nuxt jokes page'
        }
      ]
    }
  },
  data() {
    return {
      jokes: []
    }
  },
  async fetch() {

    const config = {
      headers: {
        'Accept': 'application/json'
      } 
    }

    try {
      const response = await axios.get(`https://icanhazdadjoke.com/search`, config) 
      this.jokes = response.data.results
    } catch (error) {
      console.log(error);
    }

  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          'Accept': 'application/json'
        } 
      }
      const response = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
      console.log(response.data);
      this.jokes = response.data.results
    }
  }
}
</script>

<style>

</style>
