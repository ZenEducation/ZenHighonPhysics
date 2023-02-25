<template>
  <vue-scroll-snap :fullscreen="true">
    <div class="top-1/2 fixed right-9 flex flex-col gap-5">
      <span
        class="w-4 h-4 bg-pink-500 rounded-md block cursor-pointer transition ease-in-out delay-150 hover:border-2 hover:border-pink-400 hover:bg-pink-500 hover:opacity-100 duration-100"
        :class="[
          { active: this.activeSection == index },
          { 'border-pink-600 border-4 scale-150': this.activeSection == index },
        ]"
        v-on:click="scrollToSection(index)"
        v-for="(offset, index) in offsets"
        v-bind:key="index"
        v-title="'Go to section ' + (index + 1)"
      >
      </span>
    </div>
    <div class="container flex flex-col justify-center items-center min-w-full">
      <section
        class="h-screen min-w-full flex justify-center items-center flex-col bg-yellow-300 item"
      >
        <h1 class="font-bold text-2xl">Vue.js</h1>
      </section>
      <section
        class="w-full h-screen flex justify-center items-center flex-col bg-violet-200 item"
      >
        <h1 class="font-bold text-1xl text-center max-w-6xl">
          ed ut perspiciatis unde omnis iste natus error sit voluptatem
          accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae
          ab illo inventore veritatis et quasi architecto beatae vitae dicta
          sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit
          aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos
          qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui
          dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed
          quia non numquam eius modi tempora incidunt ut labore et dolore magnam
          aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum
          exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex
          ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in
          ea voluptate velit esse quam nihil molestiae consequatur, vel illum
          qui dolorem eum fugiat quo voluptas nulla pariatur?
        </h1>
      </section>
    </div>
  </vue-scroll-snap>
</template>

<script>
import VueScrollSnap from "vue-scroll-snap";
export default {
  data() {
    return {
      inMove: false,
      //   inMoveDelay: 200,
      activeSection: 0,
      offsets: [],
    };
  },
  name: "FullPage",
  components: { VueScrollSnap },
  mounted() {
    console.log("Component Mounted");
    this.calculateSectionOffsets();
    console.log(this.offsets);
  },
  methods: {
    calculateSectionOffsets() {
      let sections = document.getElementsByTagName("section");
      let length = sections.length;

      for (let i = 0; i < length; i++) {
        let sectionOffset = sections[i].offsetTop;
        this.offsets.push(sectionOffset);
      }
    },
    scrollToSection(id, force = false) {
      if (this.inMove && !force) return false;
      this.activeSection = id;
      this.inMove = true;
      let section = document.getElementsByTagName("section")[id];
      if (section) {
        document
          .getElementsByTagName("section")
          [id].scrollIntoView({ behavior: "smooth" });
      }

      setTimeout(() => {
        this.inMove = false;
      }, this.inMoveDelay);
    },
  },
};
</script>

<style scoped></style>
