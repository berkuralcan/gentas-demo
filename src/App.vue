<template>
  <main class="global-container">
    <acHeader></acHeader>
    Hello World  
  </main>
</template>

<script>
import acHeader from './components/acHeader.vue'

import 'animate.css';

export default {
  name: 'App',
  data() {
    return {
     
    }
  },


  methods:{

  },
  components: {
    acHeader,

  }
}
</script>

<style>
@import url("./assets/styles.css");


main.global-container{
  max-width: 100vw;
}

</style>
