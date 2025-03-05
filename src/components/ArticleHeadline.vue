<template>
    <div class="article-header">
      <p class="author">Darwin Tumaneng</p>
      <h1 class="article-title">
        {{ articleTitle }}
      </h1>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        articleTitle: "Toyota Mobility Solutions PH empowers seafood wholesaler Mida Food with digital logistics platform"
      };
    }
  };
  </script>
  
  <style scoped>

  .author {
    font-size: 20px;
    font-weight: bold;
    color: red;
    margin-bottom: 5px;
    font-family: 'Roboto', sans-serif;
  }
  

  .article-title {
    font-size: 40px;
    font-weight: bold;
    color: #2b3a48;
    line-height: 1.4;
    font-family: 'Roboto', sans-serif;
  }
  </style>
  