<template>
  <ul class="menu uk-subnav uk-margin-remove">
    <template v-for='(item, index) in menu'>
      <li :class="{ 'uk-active': $route.name == item.name }" :key='index'>
        <nuxt-link :to='item.href'>
          {{ item.title }}
        </nuxt-link>
      </li>
    </template>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      menu: [
        {
          title: 'Home',
          name: 'index',
          href: '/',
          active: this.$route.name === 'home' ? true :false
        },
        {
          title: 'Location',
          name: 'location',
          href: '/location/',
          active: this.$route.name === 'location' ? true :false
        },
        {
          title: 'About',
          name: 'about',
          href: '/about/',
          active: this.$route.name === 'about' ? true :false
        },
      ]
    }
  }
}
</script>

<style></style>
