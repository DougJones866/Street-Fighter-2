<script setup>
import Characters from "./components/Characters.vue";
</script>

<template>
  <div ><h2>Street Fighter</h2></div>
  <Characters />
</template>

<style>
h2 {
  color:orangered;
}

body {
  background-image: url("../images/logo.png");
  background-size: 250px;
  background-repeat: repeat;
  background-color: blue;
  background-blend-mode: multiply;
  animation: animateBackground 40s linear infinite;
}

@keyframes animateBackground {
  from {
    background-position: 0 0; /* start at top-left corner */
  }
  to {
    background-position: 100% 100%; /* end at bottom-right corner */
  }
}


</style>
