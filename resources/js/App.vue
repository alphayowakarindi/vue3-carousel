<template>
  <Carousel :itemsToShow="3.95" :wrapAround="true" :transition="500">
    <Slide v-for="slide in slides" :key="slide.id">
      <div class="carousel__item">
        <img :src="slide.url" alt="" />
      </div>
    </Slide>

    <template #addons>
      <Navigation />
      <Pagination />
    </template>
  </Carousel>
</template>

<script>
import { defineComponent } from "vue";
import { Carousel, Pagination, Navigation, Slide } from "vue3-carousel";

import "vue3-carousel/dist/carousel.css";

export default defineComponent({
  name: "Autoplay",
  components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      slides: [
        {
          id: 1,
          title: "Vue 3 Introduction",
          content: "VueJS is a library",
          url: "/imgs/img1.jpeg",
        },
        {
          id: 2,
          title: "Vue 3 Components",
          content: "Know the components",
          url: "/imgs/img2.jpeg",
        },
        {
          id: 3,
          title: "Vue 3 Conditional",
          content: "Rendering Conditionally",
          url: "/imgs/img3.jpeg",
        },
      ],
    };
  },
});
</script>

<style scoped>
img {
  width: 100%;
}
.carousel__slide {
  padding: 5px;
}

.carousel__viewport {
  perspective: 2000px;
}

.carousel__track {
  transform-style: preserve-3d;
}

.carousel__slide--sliding {
  transition: 0.5s;
}

.carousel__slide {
  opacity: 0.9;
  transform: rotateY(-20deg) scale(0.9);
}

.carousel__slide--active ~ .carousel__slide {
  transform: rotateY(20deg) scale(0.9);
}

.carousel__slide--prev {
  opacity: 1;
  transform: rotateY(-10deg) scale(0.95);
}

.carousel__slide--next {
  opacity: 1;
  transform: rotateY(10deg) scale(0.95);
}

.carousel__slide--active {
  opacity: 1;
  transform: rotateY(0) scale(1.1);
}
</style>
