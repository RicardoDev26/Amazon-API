<template>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="currentColor"
      :class="['star', { 'star-filled': filled }]"
      @click="toggle"
    >
      <path d="M12 .587l3.668 7.43 8.203 1.193-5.92 5.759 1.394 8.138-7.345-3.864-7.345 3.864 1.394-8.138-5.92-5.759 8.203-1.193z"/>
    </svg>
  </template>
  
  <script>
  export default {
    props: {
      filled: {
        type: Boolean,
        default: false,
      },
    },
    methods: {
      toggle() {
        this.$emit('update:filled', !this.filled);
      },
    },
  };
  </script>
  
  <style scoped>
  .star {
    width: 24px;
    height: 24px;
    cursor: pointer;
    fill: transparent;
    stroke: currentColor;
    stroke-width: 2;
  }
  .star-filled {
    fill: currentColor;
  }
  </style>
  