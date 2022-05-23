<template>
  <main>
  
    <h1>Film</h1>
  <div class="cg-container">
    <div
    v-for="(item,index) in film" :key="`card-film${index}`"
    class="card-film">

      <!-- <div class="img-film">
        <img :src="item.poster_path" :alt="item.title">
      </div> -->
      <h2> Titolo: {{item.title}}</h2>
      <h3> Titolo originale: {{item.original_title}}</h3>
      <p> Lingua: {{item.original_language}}</p>
      <p> Voti: {{item.vote_count}}</p>

    </div>

  </div>

    <h1>Seriet Tv</h1>
  <div class="cg-container">

    <div
    v-for="(item,index) in serie" :key="`card-tv${index}`"
    class="card-film">

      <!-- <div class="img-film">
        <img :src="item.poster_path" :alt="item.title">
      </div> -->
      <h2> Titolo: {{item.name}}</h2>
      <h3> Titolo originale: {{item.original_name}}</h3>
      <p> Lingua: {{item.original_language}}</p>
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

  .cg-container{
    width: 90%;
    margin: auto;
    display: flex;
    flex-wrap: wrap;
    .card-film{
    width: calc(100% / 5 - 10px);
    border: 1px solid black;
    min-height: 200px;
    }
    .img-film{
      width: 80%;
    }
  
  }
</style>