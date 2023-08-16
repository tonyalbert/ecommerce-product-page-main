<template>
    <button
      class="flex bg-orange text-white space-x-3 px-5 py-3 rounded-md w-full align-center justify-center items-center shadow-2xl shadow-orange mb-5"
      @click="clickFunction"
    >
      <img class="stroke-white" src="../assets/images/icon-cart-button.svg" alt="Cart Icon">
      <span>{{ buttonText }}</span>
    </button>
  </template>
  
  <script>
  export default {
    props: {
      buttonText: String,
      clickFunction: Function, 
    },
  };
  </script>
  