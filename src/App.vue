<template>
  <img :src="imageUrl" alt="image-1" class="image1">
  <DateBadge class="date-badge"></DateBadge>
</template>

<script>
import DateBadge from './components/date-badge.vue'

export default {
  name: 'App',
  components: {
    DateBadge
  },
  data() {
    return {
      imageUrl: require('@/assets/tmsph-ls-midafood.jpeg') 
    };
  }
}
</script>

<style>
.image1 {
  width: 1500px; 
  height: auto;  
}

.date-badge{
  position: absolute;
  top: -20px; 
  left: 20px; 
}
</style>
