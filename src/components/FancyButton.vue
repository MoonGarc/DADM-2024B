<template>
    <button> 
      <slot></slot> 
    </button>
  </template>
  <style scoped>
  .content{
    text-align: center;
  }
  button{
    width: 12rem;
    margin: 30px auto;
    font-size: 2rem;
  }
  </style>