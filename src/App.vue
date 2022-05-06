<template>
  <div id="app">
    <HeaderApp/>
    <MainApp/>
  </div>
</template>

<script>
import HeaderApp from "./components/HeaderApp.vue"
import MainApp from "./components/MainApp.vue"

export default {
  name: 'App',
  components: {
    HeaderApp,
    MainApp,
  },
}
</script>

<style lang="scss">
  @import "./style/general.scss";
</style>
