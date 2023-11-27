<template>
  <div class="container d-flex align-center justify-center flex-wrap">
    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Bomdod</h2>
      <p class="text-h6">Vaqt: {{ this.tong_saharlik }}</p>
    </v-sheet>

    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Quyosh</h2>
      <p class="text-h6">Vaqt: {{ this.quyosh }}</p>
    </v-sheet>

    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Peshin</h2>
      <p class="text-h6">Vaqt: {{ this.peshin }}</p>
    </v-sheet>

    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Asr</h2>
      <p class="text-h6">Vaqt: {{ this.asr }}</p>
    </v-sheet>

    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Shom</h2>
      <p class="text-h6">Vaqt: {{ this.shom_iftor }}</p>
    </v-sheet>

    <v-sheet :elevation="7" :height="200" :width="200" border color="success" rounded class="d-flex align-center justify-space-around flex-column text-center mx-auto px-4">
      <h2 class="text-h5 font-weight-black">Hufton</h2>
      <p class="text-h6">Vaqt: {{ this.hufton }}</p>
    </v-sheet>
  </div>

</template>


<style scoped>
  .container{
    width: 100vw;
    min-height: 100vh;
  }
</style>


<script>
  import axios from 'axios'
  export default {
    name: 'postList',
    data() {
      return{
        times: {},
        tong_saharlik: '',
        quyosh: '',
        peshin: '',
        asr: '',
        shom_iftor: '',
        hufton: '',
      }
    },

    created(){
      this.getPosts()
    },

    methods:{
      getPosts() {
        axios.get('https://islomapi.uz/api/present/day?region=Toshkent')
        .then((response) => {
          this.times = response.data
          console.log(this.times)
          console.log(this.times.region)
          this.tong_saharlik = this.times.times.tong_saharlik
          this.quyosh = this.times.times.quyosh
          this.peshin = this.times.times.peshin
          this.asr = this.times.times.asr
          this.shom_iftor = this.times.times.shom_iftor
          this.hufton = this.times.times.hufton
        })

        .catch((error) => {
          console.error(error);
        })
      }
    }
  }
</script>