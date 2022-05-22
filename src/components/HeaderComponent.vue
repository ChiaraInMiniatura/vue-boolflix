<template>
  <header>

  <div class="box-logo">
    <img src="../assets/img/Netflix-Logo.webp" alt=" logo">
  </div>

  <div>
    <input
    @keyup.enter="$emit('search', searchInput)"
    v-model="searchInput"
    type="text" placeholder="Cerca film o serie Tv">
  </div>

  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  
  data(){
  return{
    searchInput: ""
  }
}

}
</script>

<style lang="scss" scoped>
@import "../assets/style/global";

header{
  height: 100px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding:0 20px;
  input{
    width: 300px;
  };
  .box-logo{
    width: 200px;
  }

}

</style>