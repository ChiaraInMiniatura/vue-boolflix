<template>
  <main>
  
    <h1>Film</h1>
  <div class="cg-container">
    <div
    v-for="(item,index) in film" :key="`card-film${index}`"
    class="card">

      <div class="img-film">
        <img :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" alt="immagine non disponibile">
      </div>
      <h2> Titolo: {{item.title}}</h2>
      <h3> Titolo originale: {{item.original_title}}</h3>
       <div v-if="item.original_language == 'en'">
          <img class="bandiera" src="../assets/img/bandiera-ing.png" alt="bandiera">
        </div>
        <div v-else-if="item.original_language == 'it'">
          <img class="bandiera" src="../assets/img/bandiera-it.png" alt="bandiera it">
        </div>
        <div v-else>
          <p> Lingua: {{item.original_language}}</p>
        </div>
        
        <span>Voto: {{item.vote_average}}</span>
            
            <div class="stars" v-if="parseInt(item.vote_average)/2 > 4">
             <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
            </div>

            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 3"> 
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 2">
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 1">
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 0">
             <i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 == 0">
             <i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>

    </div>

  </div>

    <h1>Serie Tv</h1>
  <div class="cg-container">

    <div
    v-for="(item,index) in serie" :key="`card-tv${index}`"
    class="card">

      <div class="img-film">
        <img :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" alt="immagine non disponibile">
      </div>
      <h2> Titolo: {{item.name}}</h2>
      <h3> Titolo originale: {{item.original_name}}</h3>

        <div v-if="item.original_language == 'en'">
          <img class="bandiera" src="../assets/img/bandiera-ing.png" alt="bandiera">
        </div>
        <div v-else-if="item.original_language == 'it'">
          <img class="bandiera" src="../assets/img/bandiera-it.png" alt="bandiera it">
        </div>
        <div v-else>
          <p> Lingua: {{item.original_language}}</p>
        </div>
          
          <!-- ciclo per stelle che non funziona -->
          <!-- <div v-for="star in stars" :key="star">
            <i class="fa-solid fa-star"></i>
          </div>
          <div v-for="star in (5 - stars)" :key="star" >
            <i class="fa-regular fa-star"></i>
          </div> -->
      
      <span>Voto: {{item.vote_average}}</span>
            
            <div class="stars" v-if="parseInt(item.vote_average)/2 > 4">
             <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
            </div>

            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 3"> 
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 2">
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 1">
              <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 > 0">
             <i class="fa-solid fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>
            <div class="stars" v-else-if="parseInt(item.vote_average)/2 == 0">
             <i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i><i class="fa-regular fa-star"></i> 
            </div>

    </div>

  </div>

</main>
</template>

<script>

export default{
name: "MainComponent",
props: {
    film: Object,
    serie: Object,
  },
  // funzione per stelle che non funziona
  // methods: {
  //   stars() {
  //     let numStelle = Math.ceil(this.serie.vote_average / 2)
  //     return numStelle 
  // },
  
  // }
}

</script>

<style lang="scss" scoped>
@import "../assets/style/global";
  main{
    color: white;
    padding:20px;
    h1{
      margin: 15px;
    }
  }
  .cg-container{
    width: 90%;
    margin: auto;
    display: flex;
    flex-wrap: wrap;
    .card{
    width: calc(100% /4 - 20px);
    background-color:rgb(63, 62, 62) ;
    padding: 10px;
    border: 1px solid black;
    margin: 10px;
    min-height: 200px;
    h2, h3, p, img{
      margin-bottom:15px ;
    }
    }
    .img-film{
      width: 80%;
    }
    .bandiera{
      width: 30px;
    }
  
  }
</style>