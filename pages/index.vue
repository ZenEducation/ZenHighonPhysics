<template>

  <div class="bg-gray-900 text-white flex justify-evenly">
    <h1>Index Page</h1>
    <NuxtLink to="/fullPage"> Full Page</NuxtLink>

  <div>
  <div class="py-4 flex justify-evenly bg-gray-900 text-white">
    <NuxtLink to="/">Index Page</NuxtLink>
    <NuxtLink to="/about"> Profile Card </NuxtLink>

  </div>
</div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const state = reactive({
      count: 0,
    });

    return {
      ...toRefs(state),
    };
  },
};
</script>

<style lang="scss" scoped></style>
