<!-- _id index -->
<template>
  <div v-vk-height-viewport.expand>
    ID: <b>{{ $route.params.id }}</b>
    <p class="uk-text-large">{{ joke }}</p>
    <nuxt-link to="/jokes" class="uk-button uk-button-default">
      <vk-icon icon="arrow-left"></vk-icon>
      Back
    </nuxt-link>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  head() {
    return {
      title: `Joke ID: ${this.$route.params.id}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.joke
        }
      ]
    }
  },
  data() {
    return {
      joke: {}
    }
  },
  async fetch() {

    const config = {
      headers: {
        'Accept': 'application/json'
      } 
    }

    try {
      const response = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config) 
      //console.log(response.data)
      this.joke = response.data.joke
    } catch (error) {
      console.log(error);
    }

  },
}
</script>

<style>

</style>