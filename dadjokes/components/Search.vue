<template>
  <form @submit.prevent='onSubmit'>
    <vk-grid class="uk-grid-small">
      <div class="uk-width-expand@m">
        <input v-if='!useButton' class="uk-input" type="text" v-model="text" placeholder="Search..." @keyup='onPress()'  />
        <input v-else class="uk-input" type="text" v-model="text" placeholder="Search..." />
      </div>
      <div class="uk-width-auto" v-if='useButton'>
        <input type="submit" value="Search" class="uk-button uk-button-primary uk-width-medium" @click='onSubmit()' />
      </div>
    </vk-grid>
  </form>
</template>

<script>
export default {
  data() {
    return {
      text: '',
      useButton: false
    }
  },
  methods: {
    onPress() {
      if(this.text.length > 2) {
        this.$emit('search-text', this.text);
      } else {
        this.$emit('search-text', '');
      }
    },
    onSubmit() {
      this.$emit('search-text', this.text);
    }
  },
}
</script>

<style>

</style>