<template>
  <div class="uk-card uk-card-hover uk-card-body uk-text-center uk-border-rounded">
    <img :src='image' class="uk-border-circle" />
    <h3 class="uk-h4 uk-margin-small-bottom">{{ fullName }}</h3>
    <span class="uk-text-muted">{{ location }}</span>
  </div>
</template>

<script>
export default {
  props: ['image', 'gender', 'firstName', 'lastName', 'country', 'city'],
  computed: {
    fullName() {
      return this.firstName + " " + this.lastName
    },
    location() {
      return this.city + ', ' + this.country
    }
  }
}
</script>

<style>
@media(max-width: 480px) {
  .uk-card-body {
    padding: 10px !important;
  }
}
</style>