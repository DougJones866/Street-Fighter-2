<script setup>
import Characters from "./components/Characters.vue";
</script>

<template>
  <div></div>
  <Characters />
</template>

<style>


body {
  background-image: url("../images/sf2.png");
  background-size: 250px;
  background-repeat: repeat;
  background-color: #3e2e87;
  
  
  animation: animateBackground 40s linear infinite;
  
}

/* @keyframes animateBackground {
  from {
    background-position: 0 0; 
  }
  to {
    background-position: 100% 100%; 
  }
} */
</style>
