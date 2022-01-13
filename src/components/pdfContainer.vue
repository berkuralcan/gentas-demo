<template>
  <div v-if="isMobile" @touchstart="addScrollAnimation" @mousedown="addScrollAnimation" @touchend="removeScrollAnimation" @touchcancel="removeScrollAnimation" @mouseup="removeScrollAnimation" class="pdf-container">
      <div @click="documentSelected(file)" class="pdf-box" v-for="file in files" :key=file.id>
          <div class="pdf-box__container">
            <img :src="require(`../assets/${file.cover}`)" alt="image">
          </div>
      </div>
  </div>

  <div v-else class="pdf-container">
      <a target="_blank" :href="`/pdf/${file.src}`" class="pdf-box" v-for="file in files" :key=file.id>
          <div class="pdf-box__container">
            <img :src="require(`../assets/${file.cover}`)" alt="image">

          </div>
      </a>
  </div>
</template>

<script>
export default {
  name: "pdfContainer",
  props: ['files'],
  data(){
    return {
      isScrolling: false,
    }
  },

  computed: {
    isMobile: function() {
      return window.innerWidth < 850
    }
  },

  methods: {
    documentSelected(file){
      console.log("Emmiting event.")
      this.$emit("documentSelected", file)
    },

    addScrollAnimation(){
      console.log("Scroll fired")
      const pdfBoxes = document.querySelectorAll(".pdf-box")

        pdfBoxes.forEach((box) => {
        box.classList.add("scroll")
      }) 
    

    },

    removeScrollAnimation(){
        const pdfBoxes = document.querySelectorAll(".pdf-box")

        pdfBoxes.forEach((box) => {
        box.classList.remove("scroll")
      }) 
      console.log("Fired")
    }
  }
};
</script>

<style scoped>
.pdf-container {
  display: flex;
  flex-direction: column;
  font-size: 10rem;
  margin: 4rem auto;
  max-width: 90%;
  max-height: 100vh;
  overflow-y: scroll;
  background-clip: padding-box; 

  overflow-x: hidden;

  scrollbar-width: none;
  -webkit-overflow-scrolling: touch;

  padding: 1rem 0;
  
  }

.pdf-container::-webkit-scrollbar{
  display:none;
}


.pdf-box{
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  border-radius: 25px;
  transition: all .4s;
  border: 1px solid #e3e3e3;
  width: 97%;
  margin: 0 auto;
}

.scroll{
  transform: scale(1.05);
  box-shadow: rgba(0, 0, 0, 0.45) 0px 5px 15px;

}


.pdf-box img {
  border-radius: 25px;
  overflow-x: hidden;
  object-fit: cover;
  height: 500px;
  width: 100%;

}

.pdf-box:not(:first-of-type){
  margin-top: -25rem;
  position: relative;
}

@media screen and (min-width: 600px){
  .pdf-box img{
    height: 600px;
  }

  .pdf-box:not(:first-of-type){
  margin-top: -10rem;

}
}

@media screen and (min-width: 850px) {
  .pdf-container{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 20px;
    max-height: unset;
    margin: 0 auto;
    max-width: unset;
    overflow: auto;
    padding: 2rem 4rem;
}

  .pdf-box{
    border-radius: 3px;
    width: 100%;
    height: 100%;
    margin: unset;
    cursor: pointer;
  }

  .pdf-box:hover{
    transform: scale(1.04);
  }

  .pdf-box:not(:first-of-type){
  margin-top: 0;
  position: static;
}

  .pdf-box img{
    border-radius: 3px;
    width: 100%;

  }

  .scroll{
    transform: none;
    box-shadow: none;
  }
}

</style>
