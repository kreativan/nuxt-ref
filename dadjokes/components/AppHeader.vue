<template>
  <header id="header" class="uk-section uk-section-small">
    <div class="uk-container">
      <vk-grid class="uk-flex-middle">
        <div class="uk-width-expand@m">
          <div class="uk-flex uk-flex-middle">
          <span class="logo uk-margin-small-right"><Logo /></span>
            <div class="uk-h2 uk-margin-remove">Nuxt Dad Jokes</div>
          </div>
        </div>
        <div class="uk-width-auto@m">
          <ul class="uk-subnav uk-subnav-divider uk-margin-remove">
            <li>
              <nuxt-link to="/">Home</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/jokes">Jokes</nuxt-link>
            </li>
            <li>
              <nuxt-link to="/about">About</nuxt-link>
            </li>
          </ul>
        </div>
      </vk-grid>
    </div>  
  </header>
</template>

<script>
export default {

}
</script>

<style>
#header .NuxtLogo {
  width:36px;
  height:36px;
}
</style>