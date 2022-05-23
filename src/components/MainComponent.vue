<template>
  <main>
  
    <h1>Film</h1>
  <div class="cg-container">
    <div
    v-for="(item,index) in film" :key="`card-film${index}`"
    class="card-film">

      <div class="img-film">
        <img :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" :alt="item.title">
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
      <p> Voti: {{item.vote_count}}</p>

    </div>

  </div>

    <h1>Serie Tv</h1>
  <div class="cg-container">

    <div
    v-for="(item,index) in serie" :key="`card-tv${index}`"
    class="card-film">

      <div class="img-film">
        <img :src= "`https://image.tmdb.org/t/p/original/${item.backdrop_path}`" :alt="item.title">
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
             
      <p> Voti: {{item.vote_count}}</p>

    </div>

  </div>

</main>
</template>

<script>
export default {
name: "MainComponent",
props: {
    film: Array,
    serie: Array,
  }

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
    .card-film{
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