<template>
    <li class="relative border-b-2 border-gray-200">
      <button type="button" class="w-full py-4 text-left" @click="selected = !selected">
        <div class="flex items-center justify-between">
          <span class="font-medium">{{ accordion.title }}</span>
          <font-awesome-icon v-if="selected" icon="fa-solid fa-chevron-up"/>
          <font-awesome-icon v-else icon="fa-solid fa-chevron-down"/>
        </div>
      </button>
  
      <transition name="slide">
        <div v-if="selected" class="relative overflow-hidden transition-all duration-700" style="">
          <div class="py-2">
            <p class="text-sm text-gray-700 tracking-wide leading-relaxed">
              {{ accordion.description }}
            </p>
          </div>
        </div>
      </transition>
    </li>
  </template>
  <script>
  export default {
    name: 'Accordion',
    props: {
      accordion: {
        type: Object,
        required: true,
      },
    },
    data() {
      return {
        selected: false,
      }
    },
  }
  </script>
  