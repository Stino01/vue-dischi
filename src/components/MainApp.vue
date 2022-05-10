<template>
  <main>
    <InputApp @performSearch="mySearch" :albumGenre="genere"/>
    <div class="container">
        <div class="box" v-for="item in filteredList" :key="item.id">
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
    <LoaderComponent v-if="loading"/>
  </main>
</template>

<script>
import axios from 'axios'
import InputApp from "./InputApp.vue"
import LoaderComponent from "./LoaderComponent.vue"

export default {
  name: 'MainApp',
  components: {
      InputApp,
      LoaderComponent
  },
  data() {
      return {
          charactherList: [],
          searchText: '',
          genere: [],
          loading: false
      }
  },
  methods: {
      mySearch(text){
          this.searchText = text
          //console.log(this.searchText)
      }
  },
  computed: {
    filteredList(){
        if (this.searchText === '') {
            return this.charactherList;
        }

        return this.charactherList.filter((el)=> {
            return el.genre === this.searchText
        })
    }
  },
  created() {
    this.loading = true
        axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((res) => {
            this.charactherList = res.data.response
            this.loading = false;
            this.charactherList.forEach((el)=>{
                if(!this.genere.includes(el.genre)) {
                    this.genere.push(el.genre)
                }
            })
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
        background-color: $color-blue;
        position: relative;

        .container {
            width: 60%;
            margin: 0 auto;
            padding: 4em 0 8vh 0;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1em;

            .box {
                width: 18%;
                max-width: 18%;
                height: 350px;
                flex: 0 0 auto;
                background-color: $color-lightblue;
                overflow: hidden;

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
                    margin: 0 1em;
                    font-size: 1em;
                    overflow: hidden;
                }

                .sub {
                    text-align: center;
                    color: #808080;
                    padding: 1em 0;
                    width: 100%;
                }
            }
        }
    }

    @media screen and (max-width: 1200px) {
        main .container .box {
            width: 22%;
            max-width: 22%;
        }
    }
    @media screen and (max-width: 768px) {
        main .container .box {
            width: 30%;
            max-width: 30%;
        }
    }
        @media screen and (max-width: 425px) {
        main .container .box {
            width: 46%;
            max-width: 46%;
        }
    }
</style>