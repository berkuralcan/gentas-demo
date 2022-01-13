<template>
  <main class="global-container">
    <acHeader></acHeader>
    <img width="28" class="back-button" @click="isDocumentSelected = false; selectedFile = null" src="./assets/previous.png" v-if="isDocumentSelected">

    <transition enter-active-class="animate__animated animate__fadeIn animate__fast">
      <pdf-container key="1" @documentSelected="changeComponent" v-if="!isDocumentSelected" :files="files"></pdf-container>
      <single-file-viewer key="2" :file="selectedFile" v-else></single-file-viewer>
    </transition>

  
  </main>
</template>

<script>
import acHeader from './components/acHeader.vue'
import pdfContainer from './components/pdfContainer.vue'
import singleFileViewer from "./components/singleFileViewer.vue"
import 'animate.css';

export default {
  name: 'App',
  data() {
    return {
      isDocumentSelected: false,
      currentComponent: pdfContainer,
      selectedFile: null,
      files: [
          {
              id: 0,
              name: "Gentaş Okul Uygulamaları", 
              cover: "okul.jpg", 
              src: "gentas_okul_uygulamalari_vrs14.pdf" 
          },
          {
              id: 1,
              name: "Gentaş Konut Uygulamaları", 
              cover: "konut.jpg", 
              src: "gentas_konut_uygulamalari_vrs5.pdf"
          },
          {
              id: 2,
              name: "Werzalit", 
              cover: "werzalit.jpg", 
              src: "werzalit.pdf"
          },

          {
              id: 3,
              name: "Design", 
              cover: "design.jpg", 
              src: "design.pdf" 
          },

          {
              id: 4,
              name: "Gentaş Clareo", 
              cover: "clareo.jpg", 
              src: "clareo.pdf" 
          },
        ],
    }
  },


  methods:{
    changeComponent(file){
      console.log("Running main function")
      this.isDocumentSelected = true
      this.selectedFile = file    
      }
  },
  components: {
    acHeader,
    pdfContainer,
    singleFileViewer,
  }
}
</script>

<style>
@import url("./assets/styles.css");


main.global-container{
  max-width: 100vw;
}


.back-button{
  position: absolute;
  top: 2.3rem;
  right: 1.6rem;
}

</style>
