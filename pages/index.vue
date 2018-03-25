<template>
  <section class="container">
    <div>
      <app-logo/>
      <h1 class="title">
        SSR VUE-NUXT project sructure
      </h1>
      <Main-Component/>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import MainComponent from '~/components/MainComponent.vue'

export default {
  components: {
    AppLogo,
    MainComponent
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 23px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
