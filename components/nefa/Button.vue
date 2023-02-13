<template>
    <button
      class="text-sm text-center rounded-full hover:shadow-md hover:shadow-[#0c66ee]/50 transition duration-300"
      v-bind="$attrs"
      v-on="$attrs"
    >
      <slot></slot>
    </button>
  </template>
  <script>
  export default {
    name: 'Button',
    inheritAttrs: false,
  }
  </script>
  