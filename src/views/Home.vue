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
            carouselRuns: true,
           
        }
    },
	mounted: function(){
		this.runCarousel();
	},
	watch:{
		carouselRuns: function(val){
			if(val){
				this.runCarousel();
			} else{
				this.stopCarousel();
			}
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
        this.carouselRuns = false
      },
      mouseleave(){
        this.carouselRuns = true
      },
	runCarousel(){
        this.carouselInterval = setInterval(() => this.next(), 2000);
      },
	stopCarousel(){
		clearInterval(this.carouselInterval);
    },
    },
    components : {
        Carousel,
        CarouselSlide,
    }
}
</script>

<style scoped>
#carousel-img {
  width: 100%;
  height: 300px;
  
}
</style>