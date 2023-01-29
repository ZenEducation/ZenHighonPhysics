<script>

  export default {
    data() {
    return{
    inMove: false,
    inMoveDelay: 400,
    activeSection: 0,
    offsets: [],
    touchStartY: 0
    }
  },
  mounted() {
    console.log("asdf ");
    this.calculateSectionOffsets();
    console.log(this.offsets);
    window.addEventListener('sccroll', this.handleMouseWheelDOM);     
    document.onmousewheel=this.handleMouseWheelDOM;
   
  },
  methods: {
    
    calculateSectionOffsets() {
      let sections = document.getElementsByTagName('section');
      let length = sections.length;
      
      for(let i = 0; i < length; i++) {
        let sectionOffset = sections[i].offsetTop;
        this.offsets.push(sectionOffset);
      }
    },
     handleMouseWheelDOM: function(event) {
      event.preventDefault();   
      console.log(Math.floor(event.pageY/window.innerWidth));
      let section = document.getElementsByTagName('section')[Math.floor(event.pageY/window.innerWidth)];
      if(section) {
        document.getElementsByTagName('section')[Math.floor(event.pageY/window.innerWidth)].scrollIntoView({behavior: 'smooth'});
      }
      
      setTimeout(() => {
        this.inMove = false;
      }, this.inMoveDelay);
    },
    moveDown() {
      if(this.activeSection<this.offsets.length && this.activeSection>0){
      this.activeSection--;
      console.log(this.activeSection);
      let section = document.getElementsByTagName('section')[this.activeSection];
      if(section) {
        document.getElementsByTagName('section')[this.activeSection].scrollIntoView({behavior: 'smooth'});
      }
      
      setTimeout(() => {
        this.inMove = false;
      }, this.inMoveDelay);
      }
    },
    moveUp() {
      if(this.activeSection>=0 && this.activeSection<this.offsets.length ){
      this.activeSection++;
      console.log(this.activeSection);
      let section = document.getElementsByTagName('section')[this.activeSection];
      if(section) {
        document.getElementsByTagName('section')[this.activeSection].scrollIntoView({behavior: 'smooth'});
      }
      
      setTimeout(() => {
        this.inMove = false;
      }, this.inMoveDelay);
    }
    }
  }, 
  
    name: 'FullScreenScroll',  
  }
</script>

<template>
   <div class="overflow-hidden">
    <div class="fixed inset-3">
    <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-l left-0 right-0"
    v-on:click="moveDown" >
    Prev
    </button>
    <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-r"
    v-on:click="moveUp">
        Next
    </button>
    </div>
    
    <section class="h-screen flex justify-center items-center flex-col bg-cyan-600">
      <h1 class="font-bold text-2xl">Vue.js Fullpage Scroll</h1>
    </section>

    <section class="h-screen flex justify-center items-center flex-col bg-cyan-500">
      <h1 class="font-bold text-2xl">Section 2</h1>
    </section>
    <section class="h-screen flex justify-center items-center flex-col bg-cyan-400">
      <h1 class="font-bold text-2xl">Section 3</h1>
    </section>
    <section class="h-screen flex justify-center items-center flex-col bg-cyan-300">
      <h1 class="font-bold text-2xl">Section 4</h1>
    </section>
    <section class="h-screen flex justify-center items-center flex-col bg-cyan-200">
      <h1 class="font-bold text-2xl">Section 5</h1>
    </section>
    </div>
</template>

