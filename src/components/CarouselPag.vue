<template>
   <div class="carousel-container">
      <div class="carousel">
        <div class="slides">
          <img
            src="../assets/imagenes/carr1.jpeg"
            alt="Image 1"
          />
          <img
            src="../assets/imagenes/carr2.jpg"
            alt="Image 2"
          />
          <img
            src="../assets/imagenes/carr3.jpg"
            alt="Image 3"
          />
        </div>
        <button class="prev" @click="prevSlide">&#10094;</button>
        <button class="next" @click="nextSlide">&#10095;</button>
      </div>
    </div>
    <br> 
    <div class="container-fluid text-center" id="todoslosprod">
      <p class="bien"><strong>!BIENVENID@S AL COYOTITO!</strong></p>
      <p class="expl">
        EXPLORA NUESTRAS SECCIONES Y ENCUENTRA JUSTO LO QUE ESTAS BUSCANDO !GRACIAS POR VISITARNOS!
      </p>
    </div>
  </template>
  
  <script>
  import carr1 from '../assets/imagenes/carr1.jpeg';
  import carr2 from '../assets/imagenes/carr2.jpg';
  import carr3 from '../assets/imagenes/carr3.jpg';

export default {
  name: 'CarouselPag',
  data() {
    return {
      currentIndex: 0,
      slideInterval: null,
      images: [
        { src: carr1, alt: 'Image 1' },
        { src: carr2, alt: 'Image 2' },
        { src: carr3, alt: 'Image 3' }
      ]
    };
  },
  methods: {
    showSlide(index) {
      const slides = this.$el.querySelector('.slides');
      const totalSlides = this.images.length;

      if (index >= totalSlides) {
        this.currentIndex = 0;
      } else if (index < 0) {
        this.currentIndex = totalSlides - 1;
      } else {
        this.currentIndex = index;
      }

      const offset = -this.currentIndex * 100;
      slides.style.transform = `translateX(${offset}%)`;
    },
    nextSlide() {
      this.showSlide(this.currentIndex + 1);
    },
    prevSlide() {
      this.showSlide(this.currentIndex - 1);
    },
    startSlideShow() {
      this.slideInterval = setInterval(this.nextSlide, 7000); // Cambia de imagen cada 3 segundos
    }
  },
  mounted() {
    this.showSlide(this.currentIndex);
    this.startSlideShow();
  },
  beforeDestroy() {
    if (this.slideInterval) {
      clearInterval(this.slideInterval);
    }
  }
};
  </script>
  
  <style scoped>
  .carousel-container {
    width: 90%;
    max-width: 1350px;
    position: relative;
    margin: 0 auto;
  }
  
  .carousel {
    overflow: hidden;
    position: relative;
    height: 650px;
  }
  
  .slides {
    display: flex;
    transition: transform 0.5s ease;
    height: 100%;
  }
  
  .slides img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
  
  button.prev,
  button.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    color: rgb(242, 174, 174);
    border: none;
    padding: 10px;
    cursor: pointer;
    z-index: 1;
  }
  
  button.prev {
    left: 10px;
  }
  
  button.next {
    right: 10px;
  }
  
  button:focus {
    outline: none;
  }
/*Bienvenida */
  #todoslosprod {
  background-color: #ffd0d7;
  padding: 3px;

  .bien {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 20px;
    color: rgb(70, 70, 70);
    text-align: center;
  }
}
  </style>