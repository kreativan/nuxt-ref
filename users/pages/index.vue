<!-- Users index -->
<template>
  <div class="uk-container">
    <h1 class="uk-text-center">Random People</h1>
    <div class="uk-background-muted uk-padding uk-margin-medium">
      <Search @search-text='userSearch' @select-gender='filterGender' />
    </div>
    <div v-if="spinner" class="uk-padding-large uk-text-center uk-text-primary">
      <vk-spinner ratio="1.5"></vk-spinner>
    </div>
    <vk-grid class="uk-child-width-1-5@l uk-child-width-1-4@m uk-child-width-1-3@s uk-child-width-1-2 uk-grid-small">
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
    <div class="uk-margin-medium uk-text-center">
      <nuxt-link to="/location/" class="uk-button uk-button-primary uk-button-large">Browse More Users</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: 'Home',
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
      users: [],
      spinner: true,
      seed: 'kreativan' // use it &seed=this.seed to always fetch save users
    }
  },
  async fetch() {
    const response = await fetch(`https://randomuser.me/api/?results=10&gender=`)
    const data = await response.json()
    // console.log(data.results)
    this.users = data.results
    this.spinner = false;
  },
  methods: {
    async userSearch(text, gender) {

      const response = await fetch(`https://randomuser.me/api/?results=10&gender=${gender}`)
      const data = await response.json()
      //console.log(data);
      this.users = data.results
      this.spinner = false;
  
    },
    async filterGender(gender) {
      const response = await fetch(`https://randomuser.me/api/?results=10&gender=${gender}`)
      const data = await response.json()
      //console.log(data);
      this.users = data.results
      this.spinner = false;
    }
  }
}
</script>

<style></style>
