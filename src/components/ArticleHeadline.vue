<template>
  <div class="article-container">
    <div class="image-wrapper">
      <DateBadge class="badge-position" />
      <img v-if="selectedArticle.image_url" :src="getImageUrl(selectedArticle.image_url)" alt="Article Image" class="article-image">
      <ShareButton></ShareButton>
      <div id="divider"></div>
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
import ShareButton from '@/components/ShareButton.vue'

export default {
  components: {
    DateBadge,
    ShareButton
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
  font-size: 20px;
}
.article-container {
  position: relative;
  width: 97%;
  margin-left: 10px;
  margin-top: -55px;
}

.article-header{
  font-family: 'Roboto', sans-serif;
}

.article-desc{
  font-family: 'Roboto', sans-serif;
  font-size: 15px;
}


.image-wrapper {
  position: relative;
  width: 100%;
  display: inline-block;
}

.article-image {
  width: 100%;
  max-height: 600px;
  object-fit: cover;
  margin-left: 10px;
}

.badge-position {
  position: absolute;
  top: 615px !important; 
  left: 10px; 
  z-index: 20;
}


.read-article{
  font-family: 'Roboto', sans-serif;
  text-decoration: underline;
  font-weight: bold;
  color: rgba(46, 45, 45, 0.931); 
}
#divider{
  width: 1390px; 
  height: 2px;  
  background-color: rgba(143, 142, 142, 0.393); 
  margin-top: 20px; 
}

@media (max-width: 768px) {
  .article-container{
    margin-top: -65px;
  }
  .article-image{
    max-width: 500px;
    display: block;
    margin-left: -1px;
  }

  .article-header{
    font-family: 'Roboto', sans-serif;
    font-size: 13px;
  }

  #divider{
    width: 385px; 
    height: 2px;  
    background-color: rgba(143, 142, 142, 0.393); 
    margin-top: 20px; 
  }
}
</style>