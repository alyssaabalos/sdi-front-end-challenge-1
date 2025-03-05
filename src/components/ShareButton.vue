<template>
    <div class="share-container">
      <svg class="share-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 15.84" width="20" height="15.84">
        <polygon class="cls-1" points="13.41 13.21 20 6.61 13.41 0 13.41 13.21"/>
        <path class="cls-1" d="M13.42,8.8l-.77-.11c-.45-.06-1.1-.15-1.86-.19a12.19,12.19,0,0,0-2.54.08,10.48,10.48,0,0,0-1.39.28,9.12,9.12,0,0,0-1.38.54,9.46,9.46,0,0,0-1.31.76,10.43,10.43,0,0,0-1.14,1,8.28,8.28,0,0,0-1,1.09,8.33,8.33,0,0,0-.76,1.09c-.21.36-.42.68-.58,1l-.38.81L0,15.84l.13-.77.15-.9c.07-.34.19-.72.3-1.15a9.13,9.13,0,0,1,.47-1.35,9.53,9.53,0,0,1,.7-1.47,12.18,12.18,0,0,1,1-1.49A12.08,12.08,0,0,1,5.59,6.18a13.67,13.67,0,0,1,1.66-.87,15.88,15.88,0,0,1,3.14-1c.93-.21,1.7-.31,2.24-.39l.78-.11Z"/>
      </svg>
      <p class="share-btn">SHARE</p>
    </div>
  </template>
  
 <style>
    .share-container 
    {
        display: flex;
        align-items: center; 
        justify-content: flex-end; 
        gap: 5px; 
        width: 100%;
    }

    

    .share-icon {
        width: 16px; 
        height: auto;
        margin-right: 4px; 
    }
    
    .cls-1 {
        fill: #8e8e8e;
    }
    
    .share-btn {
        color: rgba(77, 75, 75, 0.861);
        font-family: 'Open Sans', sans-serif;
        cursor: pointer;
    }
</style>