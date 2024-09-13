<template>
    <div>
      <div :style="{ backgroundColor: color, width: '100px', height: '100px', margin: '20px auto' }"></div>
      <button @click="changeColor">Change Box Color</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      color: String
    },
    emits: ['change-color'],
    setup(props, { emit }) {
      const changeColor = () => {
        emit('change-color');
      };
  
      return {
        changeColor
      };
    }
  };
  </script>
  