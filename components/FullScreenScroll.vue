<template>
  <vue-scroll-snap :fullscreen="true">
    <div class="fixed">
      <button
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-l left-0 right-0"
        v-on:click="moveUp"
      >
        Prev
      </button>
      <button
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-r"
        v-on:click="moveDown"
      >
        Next
      </button>
    </div>
    <section
      class="h-screen flex justify-center items-center flex-col bg-cyan-600 item"
    >
      <h1 class="font-bold text-2xl">Vue.js</h1>
    </section>
    <section
      class="w-full h-screen flex justify-center items-center flex-col bg-violet-200 item"
    >
      <h1 class="font-bold text-1xl text-center">
        ed ut perspiciatis unde omnis iste natus error sit voluptatem
        accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
        illo inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
        odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
        voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
        quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
        eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
        voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
        corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
        Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse
        quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
        voluptas nulla pariatur?
      </h1>
    </section>
    <section
      class="w-full h-screen flex justify-center items-center flex-col bg-violet-900 item"
    >
      <h1 class="font-bold text-1xl text-center">
        ed ut perspiciatis unde omnis iste natus error sit voluptatem
        accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
        illo inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
        odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
        voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
        quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
        eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
        voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
        corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
        Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse
        quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
        voluptas nulla pariatur?
      </h1>
    </section>

    <section class="w-full h-screen flex justify-center item">
      <div
        id="LHS"
        class="w-1/2 h-screen flex justify-center items-center bg-yellow-600"
      >
        <h1 class="font-bold text-2xl items-center underline">
          Artificial intelligence
        </h1>
      </div>

      <section id="RHS1" class="w-1/2 h-screen bg-red-200 overflow-y-auto item">
        <div class="w-full h-screen justify-center items-center bg-yellow-200">
          <h1
            class="font-bold text-1xl item center justify-content text-center indent-2.5"
          >
            artificial intelligence (AI), the ability of a digital computer or
            computer-controlled robot to perform tasks commonly associated with
            intelligent beings. The term is frequently applied to the project of
            developing systems endowed with the intellectual processes
            characteristic of humans, such as the ability to reason, discover
            meaning, generalize, or learn from past experience. Since the
            development of the digital computer in the 1940s, it has been
            demonstrated that computers can be programmed to carry out very
            complex tasks—as, for example, discovering proofs for mathematical
            theorems or playing chess—with great proficiency. Still, despite
            continuing advances in computer processing speed and memory
            capacity, there are as yet no programs that can match human
            flexibility over wider domains or in tasks requiring much everyday
            knowledge.
          </h1>
        </div>

        <section
          id="RHS2"
          class="w-full h-screen justify-center items-center bg-pink-300"
        >
          <h1 class="font-bold text-1xl text-center">
            On the other hand, some programs have attained the performance
            levels of human experts and professionals in performing certain
            specific tasks, so that artificial intelligence in this limited
            sense is found in applications as diverse as medical diagnosis,
            computer search engines, and voice or handwriting recognition.
          </h1>
        </section>
      </section>
    </section>

    <section
      class="w-full h-screen flex justify-center items-center flex-col bg-violet-200 item"
    >
      <h1 class="font-bold text-1xl text-center">
        ed ut perspiciatis unde omnis iste natus error sit voluptatem
        accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab
        illo inventore veritatis et quasi architecto beatae vitae dicta sunt
        explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
        odit aut fugit, sed quia consequuntur magni dolores eos qui ratione
        voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum
        quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam
        eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
        voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam
        corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
        Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse
        quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo
        voluptas nulla pariatur?
      </h1>
    </section>
  </vue-scroll-snap>
</template>

<script>
import VueScrollSnap from "vue-scroll-snap";
export default {
  data() {
    return {
      inMoveDelay: 200,
      activeSection: 0,
      offsets: [],
    };
  },
  components: { VueScrollSnap },
  name: "FullScreenScroll",
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
    moveUp() {
      if (this.activeSection < this.offsets.length && this.activeSection > 0) {
        this.activeSection--;
        console.log(this.activeSection);
        let section =
          document.getElementsByTagName("section")[this.activeSection];
        if (section) {
          section.scrollIntoView({ behavior: "smooth" });
        }
      }
    },
    moveDown() {
      if (
        this.activeSection >= 0 &&
        this.activeSection < this.offsets.length - 1
      ) {
        this.activeSection++;
        console.log(this.activeSection);
        let section =
          document.getElementsByTagName("section")[this.activeSection];
        if (section) {
          section.scrollIntoView({ behavior: "smooth" });
        }
      }
    },
  },
};
</script>

<style scoped>
.welcome-title {
  height: 200vh;
  display: flex;
  justify-content: center;
}
</style>
