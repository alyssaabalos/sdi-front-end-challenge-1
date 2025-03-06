<template>
    <div class="date-badge">
      <div class="date-number">{{ day }}</div>
      <div class="date-month">{{ month }}</div>
      <div class="triangle"></div>
    </div>
  </template>
  
  <script>
import { ref } from 'vue';

// eslint-disable-next-line no-unused-vars
import { computed, watch } from 'vue'; 

export default {
  data() {
    return {
      articles: [],
      selectedArticleId: null, 
      day: ref(null),
      month: ref(null),
    };
  },

  computed: {
    selectedArticle() {
      return this.articles.find(article => article.id === this.selectedArticleId) || {};
    }
  },

  async created() {
    try {
      const response = await fetch('/news.json');
      this.articles = await response.json();

      if (this.articles.length > 0) {
        this.selectedArticleId = this.articles[0].id;
      }
    } catch (error) {
      console.error("Error loading JSON:", error);
    }
  },

  watch: {
    selectedArticle(newArticle) {
      if (newArticle && newArticle.created_at) {
        const createdAt = new Date(newArticle.created_at);
        this.day = createdAt.getDate();
        this.month = createdAt.toLocaleString('en-US', { month: 'short' }).toUpperCase();
      }
    }
  }
};
</script>

  
  
  <style scoped>
  .date-badge {
    width: 90px;
    height: 90px;
    background-color: red;
    color: white;
    font-weight: bold;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;
    transform: skew(-10deg);
    border-radius: 0px;
    font-family: Arial, sans-serif;
    margin-left: 20px;
  }
  
 
  .date-number {
    font-size: 30px;
    font-weight: bold;
    line-height: 1;
  }
  
  .date-month {
    font-size: 12px;
    text-transform: uppercase;
    margin-top: -4px;
  }
  

  .triangle {
    position: absolute;
    bottom: 5px;
    right: 4px;
    width: 15px;
    height: 15px;
    background-color: white;
    clip-path: polygon(100% 0, 0 100%, 100% 100%);
  }

  @media (max-width: 768px) {
    .date-badge {
      transform: translateY(-280px); 
      width: 70px;
      height: 70px;
      margin-left: 2px;
    }
  }

  </style>
  