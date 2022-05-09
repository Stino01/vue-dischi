<template>
  <div>
    <select name="genere" id="genere" v-model="inputText" @change="changeSearch">
        <option value="">All</option>
        <option :value="genre" v-for="(genre, index) in albumGenre" :key="index">{{genre}}</option>
    </select>
  </div>
</template>

<script>

export default {
  name: 'InputApp',
  data(){
      return {
          inputText: '',
      }
  },
  props:['albumGenre'],
  methods: {
    changeSearch() {
      this.$emit('performSearch', this.inputText)
    }
  }
}
</script>

<style lang="scss">
  @import "../style/variable.scss";

  select {
    position: absolute;
    top: 4vh;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 300px;
    height: 2em;
    background-color: $color-lightblue;
    border: none;
    color: $color-white;
    text-align: center;
    border-radius: 10px;
  }
</style>
