<template>
  <header class="gentas-header">
    <img src="../assets/logo.png" alt="logo" width="200">
  </header>
</template>

<script>
export default {
  name: 'acHeader',
}
</script>

<style scoped>
header.gentas-header{
  height: 10vh;
  background-color: white;
  display:flex;
  align-items: center;
  padding-left: 2rem;
}

header.gentas-header img{
  padding-top: 10px;
}

@media screen and (min-width: 850px){
  header.gentas-header{
    padding-left: 4rem;
  }
}
</style>
