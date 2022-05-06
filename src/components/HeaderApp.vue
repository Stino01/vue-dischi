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
        height: 8vh;
        background-color: $color-lightblue;
        display: flex;
        align-items: center;

        img {
            width: 50px;
            margin-left: 20px;
        }
    }
</style>