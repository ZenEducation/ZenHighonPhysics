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
  
    name: 'SectionScroll',  
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

     
</div>
</template> 

<style scoped>
.welcome-title{
  height: 300vh;
  display: flex;
  justify-content: center;
}
.about-title{
  width: 50%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
}
.about-pages{
  width: 50%;
}
.about-pages section{
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
}
.about-pages section p{
  width: 80%;
  font-size: 18px;
  line-height: 30px;
}
.about-pages section:nth-child(1){
  background-color:rgb(212, 241, 138) ;
}
.about-pages section:nth-child(2){
  background-color:rgb(191, 242, 80) ;
}
.about-pages section:nth-child(3){
  background-color:rgb(134, 200, 34) ;
}
.about-pages div:nth-child(4){
  background-color:rgb(209, 230, 22) ;
}

</style>