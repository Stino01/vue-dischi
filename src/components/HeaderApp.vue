<template>
  <header>
      <img src="../assets/spotify-logo.svg" alt="logo">
  </header>
</template>

<script>

export default {
  name: 'HeaderApp',
}
</script>

<style lang="scss">
    @import "../style/variable.scss";

    header {
        width: 100%;
        background-color: $color-lightblue;
        display: flex;
        align-items: center;

        img {
            width: 50px;
            margin: 1em 0 1em 1em;
        }
    }
</style>