<template>

    <ProfileCard/>
<FloatingAvatar> </FloatingAvatar>
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
  
  <style scoped></style>
  


