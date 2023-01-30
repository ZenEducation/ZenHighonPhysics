<template>
    <ProfileCard/>
</template>
  
  <script>
  import { reactive, toRefs } from "vue";
  import  ProfileCard  from "../components/ProfileCard.vue";
  export default {
    setup() {
      const state = reactive({
        count: 0,
      });
      return {
        ...toRefs(state),
      };
    },
    components(){
        ProfileCard
    }
  };
  </script>
  
  <style lang="scss" scoped></style>
  