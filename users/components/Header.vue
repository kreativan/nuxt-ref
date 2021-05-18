<template>
  <header id="header" class="uk-section uk-section-small">
    <div class="uk-container">
      <vk-grid class="uk-flex-middle">
        <div class="flex-logo uk-width-expand">
          <nuxt-link to="/" class="uk-flex uk-flex-middle uk-link-reset">
            <span class="uk-margin-small-right"><Logo /></span>
            <div class="uk-h2 uk-margin-remove">People</div>
          </nuxt-link>
        </div>
        <div class="flex-menu uk-width-auto@m">
          <Menu />
        </div>
        <div class="flex-social uk-width-expand">
          <Social />
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
@media(max-width: 960px) {
  #header {
    padding: 20px 10px;
  }
  .flex-logo {
    order: 1;
  }
  .flex-menu {
    order: 3;
  }
  .flex-menu .uk-subnav {
    justify-content: center;
  }
  .flex-social {
    order: 2;
  }
}
</style>