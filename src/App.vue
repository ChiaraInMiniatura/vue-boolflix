<template>
  <div>
  <HeaderComponent  @search="searchMovie"/>
  <MainComponent :film="filmFiltrati" :serie="tvFiltrati"/>

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
      apiUrlTv:"https://api.themoviedb.org/3/search/tv",
      apiParams:{
        api_key: "175d751cc13a1117c5a81cf4f0548de9",
        language: "it-IT",
        query: " "
      },
      filmFiltrati:[],
      tvFiltrati:[],
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
    this.getApi();
    this.getApiTv();
   },
    getApiTv(){
      axios.get(this.apiUrlTv,{
        params: this.apiParams
      })
      .then(output => {
        console.log(output.data.results);
        this.tvFiltrati = output.data.results
        console.log("tv serie filtrati",this.tvFiltrati);
      })
    },
    
  },
  // mounted(){
  //   this.getApi(),
  //   this.getApiTv()
  // },
  computed:{
    SearchedMovie(){
      let movieSearched = this.output.data.results;
      console.log("serie cercate", movieSearched);
      return movieSearched
    },
    SearchedTv(){
      let tvSearched = this.output.data.results;
      console.log("serie cercate",tvSearched);
      return tvSearched
    }
  }
}
</script>

<style lang="scss">

</style>
