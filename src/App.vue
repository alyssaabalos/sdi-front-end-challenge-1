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

html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

.container {
  width: 80%;
  margin: auto;
  padding: 20px;
}


@media (max-width: 768px) {
  .container {
    width: 100%;
    padding: 10px;
    overflow-x: hidden;
  }

  .date-badge {
    font-size: 12px;
    padding: 5px;
  }
}
</style>