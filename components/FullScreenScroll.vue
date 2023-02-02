<script>
export default {
  data() {
    return {
      inMove: false,
      inMoveDelay: 200,
      activeSection: 0,
      offsets: [],
      touchStartY: 0,
    };
  },
  mounted() {
    console.log("Component Mounted");
    this.calculateSectionOffsets();
    console.log(this.offsets);
    window.addEventListener("scroll", this.handleMouseWheelDOM);
    document.onmousewheel = this.handleMouseWheelDOM;
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
    handleMouseWheelDOM: function (event) {
      event.preventDefault();
      console.log(Math.floor(event.pageY / window.innerWidth));
      let section =
        document.getElementsByTagName("section")[
          Math.floor(event.pageY / window.innerWidth)
        ];
      if (section) {
        document
          .getElementsByTagName("section")
          [Math.floor(event.pageY / window.innerWidth)].scrollIntoView({
            behavior: "smooth",
          });
      }

      setTimeout(() => {
        this.inMove = false;
      }, this.inMoveDelay);
    },
    moveDown() {
      if (this.activeSection < this.offsets.length && this.activeSection > 0) {
        this.activeSection--;
        console.log(this.activeSection);
        let section =
          document.getElementsByTagName("section")[this.activeSection];
        if (section) {
          document
            .getElementsByTagName("section")
            [this.activeSection].scrollIntoView({ behavior: "smooth" });
        }

        setTimeout(() => {
          this.inMove = false;
        }, this.inMoveDelay);
      }
    },
    moveUp() {
      if (this.activeSection >= 0 && this.activeSection < this.offsets.length) {
        this.activeSection++;
        console.log(this.activeSection);
        let section =
          document.getElementsByTagName("section")[this.activeSection];
        if (section) {
          document
            .getElementsByTagName("section")
            [this.activeSection].scrollIntoView({ behavior: "smooth" });
        }

        setTimeout(() => {
          this.inMove = false;
        }, this.inMoveDelay);
      }
    },
  },
};
</script>

<template>
  <div class="overflow-hidden">
    <div class="fixed inset-3">
      <button
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-l left-0 right-0"
        v-on:click="moveDown"
      >
        Prev
      </button>
      <button
        class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-r"
        v-on:click="moveUp"
      >
        Next
      </button>
    </div>

    <section
      class="h-screen flex justify-center items-center flex-col bg-cyan-600"
    >
      <h1 class="font-bold text-2xl">Vue.js</h1>
    </section>

    <section class="w-full h-screen flex justify-center">
      <div
        class="w-1/2 h-screen flex justify-center items-center bg-yellow-600"
      >
        <h1 class="font-bold text-2xl items-center underline">
          Artificial intelligence
        </h1>
      </div>

      <div class="w-1/2 h-screen bg-red-200 overflow-y-auto">
        <section
          class="w-full h-screen justify-center items-center bg-yellow-200"
        >
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
        </section>

        <section
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
      </div>
    </section>

    <section
      class="w-full h-screen flex justify-center items-center flex-col bg-violet-200"
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
  </div>
</template>

<style scoped>
.welcome-title {
  height: 200vh;
  display: flex;
  justify-content: center;
}
</style>
