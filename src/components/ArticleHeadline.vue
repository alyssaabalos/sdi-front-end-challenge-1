<template>
  <div class="article-container">
    <div class="image-wrapper">
      <DateBadge class="badge-position" />
      <img v-if="selectedArticle.image_url" :src="getImageUrl(selectedArticle.image_url)" alt="Article Image" class="article-image">
    </div>

    <div class="article-header">
      <p class="author">{{ selectedAuthor.name }}</p>
      <h1 class="article-title">
        {{ selectedArticle.title }}
      </h1>
      <p class="article-desc">
        {{ selectedArticle.body }}
      </p>
      
      <p class="read-article">
        READ ARTICLE
      </p>
    </div>

   
  </div>
</template>

<script>
import DateBadge from '@/components/date-badge.vue'; 

export default {
  components: {
    DateBadge
  },

  data() {
    return {
      authors: [],
      articles: [],
      selectedArticleId: null
    };
  },
  computed: {
    selectedArticle() {
      return this.articles.find(article => article.id === this.selectedArticleId) || {};
    },
    selectedAuthor() {
      return this.authors.find(author => author.id === this.selectedArticle.author_id) || {};
    }
  },

  methods: {
    getImageUrl(imageFileName) {
      return require(`@/assets/${imageFileName}`); 
    }
  },

  async created() {
    try {
      const authorsResponse = await fetch('/data.json');
      this.authors = await authorsResponse.json();

      const articlesResponse = await fetch('/news.json');
      this.articles = await articlesResponse.json();

      if (this.articles.length > 0) {
        this.selectedArticleId = this.articles[0].id;
      }
    } catch (error) {
      console.error("Error loading JSON:", error);
    }
  }
};
</script>

<style>
.author{
  margin-top: 50px;
  color: red;
}
.article-container {
  position: relative;
  width: 100%;
}

.article-header{
  font-family: 'Roboto', sans-serif;
}


.image-wrapper {
  position: relative;
  width: 100%;
  display: inline-block;
}

.article-image {
  width: 100%;
  max-height: 500px;
  object-fit: cover;
}

.badge-position {
  position: absolute;
  top: 515px !important; 
  left: 10px; 
  z-index: 20;
}
</style>