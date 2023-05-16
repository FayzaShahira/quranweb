<template>

  <li class="card" style="width: 20rem;" v-for = "(item) in infosurah">
    {{item.id + ". " + item.name_simple + " (" + item.name_arabic + ") - "}}
    {{item.verses_count + ' ayat'}}
    <p><router-link :to="{name: 'ayat', params: {id: item. id}}" class="btn btn-primary">Read</router-link></p>
  </li>

  <li class="card" v-for = "(item, index) in infoayat">
    {{item.verse_key+ " (" + item.text_uthmani + ") - "}}
  <p v-html= "infoarti[index].text"> </p>
  </li>
  <hr>
</template>

<script>
import axios from 'axios';
import {ref} from 'vue';
export default {
  data() {
    return {
      infoayat: ref([]),
      infoarti : ref ([])
    }
  },
  mounted() {
    this.getinfoayat(),
    this.getinfoarti()
  },
  methods: {
    getinfoayat() {
      axios.get('\n' + `https://api.quran.com/api/v4/quran/verses/uthmani?chapter_number=${this.$route.params.id}`)
          .then((respons) => {
            console.log(respons)
            this.infoayat = respons.data.verses
          }).catch((err) => {
        console.log('error' + err)
      })
    },

    getinfoarti() {
      axios.get('\n' + `https://api.quran.com/api/v4/quran/translations/33?chapter_number=${this.$route.params.id}`)
          .then((respons) => {
            console.log(respons)
            this.infoarti = respons.data.translations
          }).catch((err) => {
        console.log('error' + err)
      })
    }
  }
}

</script>

<style scoped>
li{
  text-align: left;
  margin-left: 50px;
  margin-right: 30px;
  list-style: none;
  margin-top: 5px;
}
</style>