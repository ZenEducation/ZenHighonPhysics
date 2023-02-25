<script>
  export default {
    data(){
        return{
        canvas: null,
        context: null,
        startX: 0,
        startY: 0,
        practicalArray: [],
        }
    },
    mounted() {
      var c = document.getElementById("c");
      this.context=c;
      var ctx = c.getContext("2d");    
      this.canvas = ctx;

      this.canvas.height = window.innerHeight;
      this.canvas.width =window.innerWidth;

      this.context.addEventListener('mousemove',this.mousemove);
      this.context.addEventListener('click',this.mousemove);
      console.log("Mounted Method ");
      this.animate();
    },
    methods :{
      handlePracticals(){
          for(let i=0;i<this.practicalArray.length;i++){
              this.practicalArray[i].update();
              this.practicalArray[i].draw(this.canvas);
              if(this.practicalArray[i].size<=0.3){
                  this.practicalArray.splice(i,1);
                  console.log(this.practicalArray.length)
                  i--;
              }
          }
      },

     animate(){
        this.canvas.fillStyle='rgba(0,0,0,0.2)';
        this.canvas.fillRect(0,0,this.context.width,this.context.height);
        this.handlePracticals();
        requestAnimationFrame(this.animate);
      },
      mousemove(e){
      for(let i=0;i<10;i++){
        this.practicalArray.push(new Practical(e.clientX,e.clientY));
      }
    },
  },
    name: 'CanvasParticals',  
  }

  class Practical{
    constructor(x,y){
        this.x=x;
        this.y=y;

        this.size=Math.random()*3+1;
        this.speedX=Math.random()* 3 -1.5;
        this.speedY=Math.random()* 3 -1.5;
    }
    update(){
      this.x+=this.speedX;
      this.y+=this.speedY;
      if(this.size>0.2) this.size-=0.1
    }
    draw(canvas){
      console.log(this.x,this.y);
        canvas.fillStyle='white';
        canvas.beginPath();
        canvas.arc(this.x,this.y,this.size,0,Math.PI*2);
        canvas.fill();
    }
  }
  </script>


<template>
    <canvas id="c">

    </canvas>
</template>
    
<style scoped>
#c{
  position: absolute;
    background: black;
}
</style>
  