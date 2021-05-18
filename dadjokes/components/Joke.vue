<template>
  <nuxt-link :to="href" class="uk-link-heading" >
    {{ index }}. {{ joke }}
  </nuxt-link>
</template>

<script>
export default {
  props: ['joke', 'id', 'index'],
  computed: {
    href() {
      return `/jokes/${this.id}/`;
    }
  }
}
</script>

<style>

</style>