<template>
    <div  >
        <carousel @next="next" @prev="prev" @mouseover="mouseover" @mouseleave="mouseleave" @running="running" >
            <carousel-slide v-for="(slide,index) in slides" 
            :key="slide" 
            :index="index" 
            :visibleSlide="visibleSlide" 
            :direction="direction"
            
             >
                <img  :src="slide" :alt="slide"  id="carousel-img">
            </carousel-slide>
           
        </carousel>
        
    </div>    
</template>

<script>
import Carousel from '../components/Carousel.vue';
import CarouselSlide from '../components/CarouselSlide';
export default {
    data(){
        return {
            slides: [
               "/img/combo1.jpeg",
               "/img/combo2.webp",
               "/img/combo3.jpg"
            ],
            visibleSlide: 0,
            direction: "",
            carouselRunning: true,
           
        }
    },
    methods: {
      next(){
        if(this.visibleSlide >= this.slides.length -1){
            this.visibleSlide = 0;
        }else{
          this.visibleSlide++
        }
        this.direction = "left"

      },
      prev(){
        if(this.visibleSlide <= 0){
            this.visibleSlide = this.slides.length -1;
        }else{
          this.visibleSlide--
        }
        this.direction = "right";
      },
      mouseover(){
        this.carouselRunning = false
      },
      mouseleave(){
        this.carouselRunning = true
      },
      running(){
         if(this.carouselRunning == true){
        var running = setInterval(() => this.next(), 2000);
        running
      }else{
        clearInterval(running)
      }
      }
     
    },
    
    
     
     
    
    
    
   
     
     
    components : {
        Carousel : Carousel,
        CarouselSlide : CarouselSlide,
    }
}
</script>

<style scoped>
#carousel-img {
  width: 100%;
  height: 300px;
  
}
</style>