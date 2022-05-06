<template>
  <main>
    <div class="container">
        <div class="box" v-for="(item, index) in charactherList" :key="index">
            <div class="img-holder">
                <img :src="item.poster" alt="">
            </div>
            <h3>{{item.title}}</h3>
            <div class="sub">
                <p>{{item.author}}</p>
                <p>{{item.year}}</p>
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  name: 'MainApp',
  data() {
      return {
          charactherList: [],
      }
  },
  mounted() {
      axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res) => {
          this.charactherList = res.data.response
      }).catch((error) => {
          console.log(error)
      })
  }
}
</script>

<style lang="scss">
    @import "../style/variable.scss";

    main {
        width: 100%;
        height: 92vh;
        background-color: $color-blue;

        .container {
            width: 60%;
            margin: 0 auto;
            padding: 8vh 0 0 0;
            display: flex;
            flex-wrap: wrap;
            gap: 1em;

            .box {
                width: 18%;
                max-width: 18%;
                height: 40vh;
                flex: 0 0 auto;
                background-color: $color-lightblue;

                .img-holder {
                    width: 80%;
                    margin: 1em auto;

                    img {
                        width: 100%;
                    }
                }

                h3 {
                    text-align: center;
                    color: $color-white;
                    text-transform: uppercase;
                }

                .sub {
                    text-align: center;
                    color: #808080;
                    padding: 1em 0;
                }
            }
        }
    }
</style>