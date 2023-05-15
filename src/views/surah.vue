<template>
  <li v-for = "(item, index) in infosurah">
    {{item.name_simple + " (" + item.name_arabic + ") - "}}
    <p v-html = "infosurah[index].verses_count+ ' ayat' "></p>
  </li>

</template>

<script>
import axios from 'axios';
import {ref} from 'vue';

export default  {
  data() {
    return{
      infosurah: ref([])
    }
  },
  mounted() {
    this.getinforsurah()
  },
  methods: {
    getinforsurah(){
      axios.get('\n' + 'https://api.quran.com/api/v4/chapters?language=id')
          .then((respons) => {
            console.log(respons)
            this.infosurah = respons.data.chapters
          }).catch((err) => {
            console.log('error' + err)
          })
    }
  }
}
</script>

<style scoped>
li{
  text-align: right;
}

</style>