<template>

  <h3>Silahkan Pilih Surah yang Ingin Dibaca</h3>
  <li class="card" style="width: 20rem;" v-for = "(item) in infosurah">
    {{item.id + ". " + item.name_simple + " (" + item.name_arabic + ") - "}}
    {{item.verses_count + ' ayat'}}
    <p><router-link :to="{name: 'ayat', params: {id: item. id}}" class="btn btn-primary">Read</router-link></p>
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
      axios.get('\n' + "https://api.quran.com/api/v4/chapters?language=id" + this.$route.params.id)
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
h6{
  text-align: left;
  margin-left: 50px;
}
h3{
  text-align: center;
  font-family: "sans-serif";
  padding: 50px;
  margin-bottom: 50px;
}
.card{
  display:inline-block;
  align-content: center;
  margin-left:70px;
}
li{
  text-align: center;
  font-weight: bold;
}
p{
  text-align: center;
  font-weight: lighter;
  margin-top: 5px;
}
.btn-primary{
  background-color: darkseagreen;
  border-color: grey;
}
</style>