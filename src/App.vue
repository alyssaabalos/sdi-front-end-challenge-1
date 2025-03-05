<template>
  <img :src="imageUrl" alt="image-1" class="image1">
  <DateBadge class="date-badge"></DateBadge>
  <div id="divider"></div>
  <ArticleHeadline></ArticleHeadline>
  <NewsPagination :totalPages="57" :currentPage="currentPage" @page-change="changePage" />
</template>

<script>
import DateBadge from './components/date-badge.vue'
import ArticleHeadline from './components/ArticleHeadline.vue';
import NewsPagination from './components/NewsPagination.vue';

export default {
  name: 'App',
  components: {
    DateBadge,
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
.image1 {
  width: 1409px; 
  height: auto;  
}

.date-badge{
  position: absolute;
  top: -20px; 
  left: 20px; 
}

#divider{
  width: 1410px; 
  height: 2px;  
  background-color: rgba(143, 142, 142, 0.393); 
  margin-top: 5px; 
}
</style>
