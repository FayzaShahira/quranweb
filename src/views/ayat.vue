<template>
  <li v-for = "(item, index) in infoayat">
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
      axios.get('\n' + 'https://api.quran.com/api/v4/quran/verses/uthmani')
          .then((respons) => {
            console.log(respons)
            this.infoayat = respons.data.verses
          }).catch((err) => {
        console.log('error' + err)
      })
    },

    getinfoarti() {
      axios.get('\n' + 'https://api.quran.com/api/v4/quran/translations/33')
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

</style>