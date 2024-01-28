<template>
    <div class="time-container">{{ formattedTime }}</div>
  </template>
  
  <script>
  export default {
    props: {
      time: Number  // in seconds
    },
    computed: {
      formattedTime() {
        const minutes = Math.floor(this.time / 60);
        const seconds = this.time % 60;
        return `${minutes}:${seconds.toString().padStart(2, '0')}`;
      }
    }
  };
  </script>
  
  <style scoped>
  /* Specific styles for this component (if needed) */
  </style>
  