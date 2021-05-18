<!-- location -->
<template>
  <div class="uk-container">
    <h1 class="uk-text-center uk-margin-medium">Choose Location</h1>
    <ul class="uk-list uk-list-striped">
      <li v-for='(country, index) in countries' :key='index'>
        <nuxt-link :to='"/location/" + country.alpha2Code.toLowerCase()' class="uk-link-heading uk-flex uk-flex-middle">
          <img :src='country.flag' width="22" height="22" />
          <span class="uk-margin-small-left">{{ country.name }}</span>
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Location',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: '',
        },
      ],
    }
  },
  data() {
    return {
      codes: 'AU;BR;CA;CH;DE;DK;ES;FI;FR;GB;IE;IR;NO;NL;NZ;TR;US',
      countries: [],
    }
  },
  async fetch() {
    console.log(this.codes)
    const response = await fetch(`https://restcountries.eu/rest/v2/alpha/?codes=${this.codes}`)
    const data = await response.json()
    // console.log(data)
    this.countries = data
  },
}
</script>

<style>

</style>