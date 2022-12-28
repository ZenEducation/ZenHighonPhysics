<script>
  export default {
    data(){
        return{
        canvas: null,
        context: null,
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
      console.log(this.canvas.height,this.canvas.width);
      this.context.addEventListener('mousemove',this.mousemove);
      this.context.addEventListener('click',this.mousemove);
      this.animate();
    },
    methods :{
      handlePracticals(){
          for(let i=0;i<this.practicalArray.length;i++){
              this.practicalArray[i].update();
              this.practicalArray[i].draw(this.canvas);
              for(let j=i;j<this.practicalArray.length;j++){
                    const dx = this.practicalArray[i].x-this.practicalArray[j].x;
                    const dy = this.practicalArray[i].y -this.practicalArray[i].y;
                    const distance=Math.sqrt(dx*dx,dy*dy);
                    if(distance<100){
                        this.canvas.beginPath();
                        this.canvas.strokeStyle=this.practicalArray[i].color;
                        this.canvas.lineWidth=0.1;
                        this.canvas.moveTo(this.practicalArray[i].x,this.practicalArray[i].y);
                        this.canvas.lineTo(this.practicalArray[j].x,this.practicalArray[j].y);
                        this.canvas.stroke();
                    }
                }
              if(this.practicalArray[i].size<=0.5){
                  this.practicalArray.splice(i,1);
                  i--;
              }
          }
      },

     animate(){
        this.canvas.fillStyle='rgba(0,0,0,0.01)';
        hue++;
        this.canvas.clearRect(0,0,this.context.width,this.context.height);
        this.handlePracticals();
        requestAnimationFrame(this.animate);
      },
      mousemove(e){
      for(let i=0;i<3;i++){
        this.practicalArray.push(new Practical(e.clientX,e.clientY));
      }
    },
  },
    name: 'ConstellationEffect',  
  }
  let hue=0;
  class Practical{
    constructor(x,y){
        this.x=x;
        this.y=y;

        this.size=Math.random()*4+1;
        this.speedX=Math.random()* 1.5 -1.5;
        this.speedY=Math.random()* 1.5 -1.5;
        this.color='hsl('+ hue +', 100%, 50%)';
    }
    update(){
        this.x+=this.speedX;
        this.y+=this.speedY;
        if(this.size>0.2) this.size-=0.1
    }
    draw(canvas){
        canvas.fillStyle=this.color;
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
  background: black;
}
</style>
  