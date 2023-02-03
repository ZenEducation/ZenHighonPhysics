
<template>
    <li class="space-y-2">
      <div class="flex items-center space-x-2">
        <font-awesome-icon icon="fa-solid fa-circle-check" color="#0c66ee" />
       
        <span>{{ title }}</span>
      </div>
      <slot></slot>
    </li>
  </template>
  <script>

  export default {
    name: 'ListItem',
    props: {
      title: {
        type: String,
        default: '',
      },
    },
  }
  </script>
  