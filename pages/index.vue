<template>
    <div class="app"> 
    <NuxtLayout>
  <NuxtPages/>
   <CalendarPicker />
  </NuxtLayout>
    </div>
  </template>
  
  <style >
  *,*:before, *:after{
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }
  
  .app{
    background: #fff;
    display: grid;
    grid-template-columns: 1;
    place-content: center;
    height: 100vh;
    /* align-items: center; */
    padding: 4rem;
  }
  </style>
  
  
  <script setup >
  
  </script> 