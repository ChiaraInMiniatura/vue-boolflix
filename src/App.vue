<template>
  <div>
  <HeaderComponent  @search="searchMovie"/>
  <MainComponent :film="filmFiltrati"/>

  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';
import axios from "axios"


export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
},

  data(){
    return{
      apiUrl: "https://api.themoviedb.org/3/search/movie",
      apiParams:{
        api_key: "175d751cc13a1117c5a81cf4f0548de9",
        language: "it-IT",
        query: " "
      },
      filmFiltrati:[]
    }
  },
  methods:{
    getApi(){
      axios.get(this.apiUrl,{
        params: this.apiParams
      })
      .then(output => {
        console.log(output.data.results);
        this.filmFiltrati = output.data.results
        console.log("film filtrati",this.filmFiltrati);
      })
    },
    searchMovie(searchInput){
      this.apiParams.query = searchInput
      console.log("ricerca utente", this.apiParams.query);
      this.getApi()
    }
  },
  mounted(){
    this.getApi()
  },
  computed:{
    SearchedMovie(){
      let movieSearched = this.output.data.results;
      console.log("film cercati", movieSearched);
      return movieSearched
    }
  }
}
</script>

<style lang="scss">

</style>
