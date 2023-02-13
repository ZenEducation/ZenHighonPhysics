<template>
  <div>
    <div class="py-4 flex justify-evenly bg-gray-900 text-white">
      <NuxtLink to="/">Index Page</NuxtLink>
      <NuxtLink to="/fullpage"> Full Page </NuxtLink>
      <NuxtLink to="/fullscreen"> Full Screen </NuxtLink>
    </div>
  </div>

  <div class="py-4 flex justify-evenly bg-gray-900 text-white">
    <NuxtLink to="/">Index Page</NuxtLink>
    <NuxtLink to="/nefaLanding"> Nefa Landing </NuxtLink>
    <NuxtLink to="/testimonials"> Testimonials Grid Section</NuxtLink>
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
