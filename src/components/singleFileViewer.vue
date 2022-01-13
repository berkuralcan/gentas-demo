<template>
  <div class="file-container">
      <div class="file-box">
          <a target="_blank" :href="`/pdf/${file.src}`">
            <img :src="require(`../assets/${file.cover}`)" alt="image">
          </a>
      </div>
  </div>
</template>

<script>
export default {
  name: "singleFileViewer",
  props: ['file']

};
</script>

<style scoped>

.file-container {
  padding-left: 1.6rem;
  padding-right: 1.6rem;
  margin-top: 4rem;
}

.file-box{
  box-shadow: rgba(14, 30, 37, 0.12) 0px 2px 4px 0px, rgba(14, 30, 37, 0.32) 0px 2px 16px 0px;

}


</style>
