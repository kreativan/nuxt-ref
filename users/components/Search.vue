<template>
  <form @submit.prevent='onSubmit'>
    <vk-grid class="uk-grid-small">
      <div class="uk-width-expand@m">
        <input class="uk-input" type="text" v-model="text" placeholder="Just type in something, search is random..." @keyup='onPress()'  />
      </div>
      <div class="uk-width-medium@m">
        <select class="uk-select" v-model="gender" @change='selectGender()'>
          <option>- Select Gender -</option>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
    </vk-grid>
  </form>
</template>

<script>
export default {
  data() {
    return {
      text: '',
      gender: '- Select Gender -'
    }
  },
  methods: {
    onPress() {
      const gender = this.gender.toLowerCase();
      if(this.text.length > 2) {
        this.$emit('search-text', this.text, gender);
      } else {
        this.$emit('search-text', '', gender);
      }
    },
    selectGender() {
      const gender = this.gender.toLowerCase();
      this.$emit('select-gender', gender);
    }
  },
}
</script>

<style>

</style>