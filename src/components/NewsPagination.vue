<template>
  <div class="pagination-container">
   
    <button class="pagination-button" disabled>‹</button>

    
    <button class="pagination-button">1</button>

   
    <button class="pagination-button">2</button>

    
    <span v-if="currentPage > 7" class="pagination-ellipsis">...</span>

   
    <button v-for="page in pagesBeforeActive" :key="page" class="pagination-button">
      {{ page }}
    </button>

   
    <button class="pagination-button active">11</button>

    
    <button v-for="page in pagesAfterActive" :key="page" class="pagination-button">
      {{ page }}
    </button>

   
    <span v-if="currentPage < totalPages - 6" class="pagination-ellipsis">...</span>

    
    <button class="pagination-button">{{ totalPages - 1 }}</button>
    <button class="pagination-button">{{ totalPages }}</button>

   
    <button class="pagination-button" disabled>›</button>
  </div>
</template>

<script>
export default {
  props: {
    totalPages: { type: Number, required: true },
    currentPage: { type: Number, required: true, default: 11 }, 
  },
  computed: {
    pagesBeforeActive() {
      return [8, 9, 10]; 
    },
    pagesAfterActive() {
      return [12, 13, 14]; 
    },
  },
};
</script>

<style scoped>
.pagination-container {
  display: flex;
  align-items: center;
  gap: 5px;
  margin-left: 10px;
}

.pagination-button {
  padding: 15px 32px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: white;
  transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out;
<<<<<<< HEAD
=======
  color: black;
>>>>>>> dev
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
  padding: 15px 32px;
  font-weight: bold;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: white;
}
<<<<<<< HEAD
=======


@media (max-width: 768px) {
  .pagination-container {
    flex-wrap: wrap; 
    justify-content: left; 
    gap: 3px; 
    display: inline-block;
  }
  

  .pagination-button, 
  .pagination-ellipsis {
    padding: 6px 10px;
    font-size: 12px; 
    min-width: 30px; 
  }
}
>>>>>>> dev
</style>
