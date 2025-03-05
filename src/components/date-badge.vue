<template>
    <div class="date-badge">
      <div class="date-number">{{ day }}</div>
      <div class="date-month">{{ month }}</div>
      <div class="triangle"></div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  

  const day = ref(13);
  const month = ref('JAN');
  </script>
  
  <style scoped>
  .date-badge {
    width: 60px;
    height: 60px;
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
  }
  
 
  .date-number {
    font-size: 20px;
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
    bottom: 4px;
    right: 4px;
    width: 10px;
    height: 10px;
    background-color: white;
    clip-path: polygon(100% 0, 0 100%, 100% 100%);
  }
  </style>
  