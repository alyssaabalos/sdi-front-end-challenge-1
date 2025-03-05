<template>
    <div class="pagination-container">
     
      <button
        @click="goToPage(currentPage - 1)"
        :disabled="currentPage === 1"
        class="pagination-button"
      >
        ‹
      </button>
  
    
      <button
        v-if="currentPage > 4"
        @click="goToPage(1)"
        class="pagination-button"
      >
        1
      </button>
  
     
      <span v-if="currentPage > 5" class="pagination-ellipsis">...</span>
  
    
      <button
        v-for="page in pagesBeforeActive"
        :key="page"
        @click="goToPage(page)"
        class="pagination-button"
      >
        {{ page }}
      </button>
  
     
      <button class="pagination-button active">
        {{ currentPage }}
      </button>
  
     
      <button
        v-for="page in pagesAfterActive"
        :key="page"
        @click="goToPage(page)"
        class="pagination-button"
      >
        {{ page }}
      </button>
  
     
      <span v-if="currentPage < totalPages - 4" class="pagination-ellipsis">...</span>
  
    
      <button
        v-if="currentPage < totalPages - 3"
        @click="goToPage(totalPages)"
        class="pagination-button"
      >
        {{ totalPages }}
      </button>
  
     
      <button
        @click="goToPage(currentPage + 1)"
        :disabled="currentPage === totalPages"
        class="pagination-button"
      >
        ›
      </button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      totalPages: { type: Number, required: true },
      currentPage: { type: Number, required: true },
    },
    computed: {
      pagesBeforeActive() {
        const start = Math.max(2, this.currentPage - 2);
        return Array.from({ length: this.currentPage - start }, (_, i) => start + i);
      },
      pagesAfterActive() {
        const end = Math.min(this.totalPages - 1, this.currentPage + 2);
        return Array.from({ length: end - this.currentPage }, (_, i) => this.currentPage + 1 + i);
      },
    },
    methods: {
      goToPage(page) {
        if (page >= 1 && page <= this.totalPages) {
          this.$emit("page-change", page);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .pagination-container {
    display: flex;
    align-items: center;
    gap: 5px;
  }
  
  .pagination-button {
    padding: 15px 32px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: white;
    transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out;
  }
  
  .pagination-button:hover {
    background-color: red;
    color: white;
  }
  
  .pagination-button.active {
    background-color: red;
    color: white;
    font-weight: bold;
    border: none;
  }
  
  .pagination-ellipsis {
    padding: 8px;
    font-weight: bold;
  }
  </style>
  