<template>

  <ArticleHeadline></ArticleHeadline>
    
  <NewsPagination :totalPages="57" :currentPage="currentPage" @page-change="changePage" />
</template>

<script>

import ArticleHeadline from './components/ArticleHeadline.vue';
import NewsPagination from './components/NewsPagination.vue';

export default {
  name: 'App',
  components: {
   
    ArticleHeadline,
    NewsPagination
  },
  data() {
    return {
      imageUrl: require('@/assets/tmsph-ls-midafood.jpeg'),
      currentPage: 11, 
  
    };
  },

  methods: {
    changePage(newPage) {
      this.currentPage = newPage;
    },
  }
}
</script>

<style>

#app {
  position: absolute;
  top: -80px !important;
  left: 0;
  width: 100%;
  margin: 12px !important;
}

.date-badge{
  position: absolute;
  top: -20px; 
  left: 20px; 
}




</style>
