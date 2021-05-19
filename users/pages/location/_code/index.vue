<!-- code -->
<template>
  <div class="uk-container">
    <h1 v-if="!spinner" class="uk-text-center uk-flex uk-flex-middle uk-flex-center">
      <img :src='location.flag' width="90" height="90"/>
      <span class="uk-margin-left">{{ location.name }}</span>
    </h1>
    <div v-if="spinner" class="uk-padding-large uk-text-center uk-text-primary">
      <vk-spinner ratio="1.5"></vk-spinner>
    </div>
    <vk-grid v-if="!spinner" class="uk-child-width-1-5@l uk-child-width-1-4@m uk-child-width-1-3@s uk-child-width-1-2 uk-margin-medium-top uk-grid-small">
      <div v-for='(user, index) in users' :key="index">
        <Card
          :image="user.picture.large"
          :gender="user.gender"
          :firstName="user.name.first"
          :lastName="user.name.last"
          :country="user.location.country"
          :city="user.location.city"
        />
      </div>
    </vk-grid>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.location.name,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'People in ' + this.location.name,
        },
      ],
    }
  },
  data() {
    return {
      code: this.$route.params.code,
      spinner: true,
      location: {},
      users: [],
    }
  },
  async fetch() {

    try {
      const get_countries = await fetch(`https://restcountries.eu/rest/v2/alpha/${this.code}`)
      const locationData = await get_countries.json()
      // console.log(data)
      this.location = locationData 
    } catch (error) {
      console.log(error)
    }

    try {
      const get_users = await fetch(`https://randomuser.me/api/?nat=${this.code}&results=20`)
      const usersData = await get_users.json()
      //console.log(usersData.results);
      this.users = usersData.results 
    } catch (error) {
      console.log(error)
    }
    
    this.spinner = false;

  },
}
</script>

<style>

</style>