<template>

  <div class="section gallery" id="gallery">
    <h2 class="section-header">GALERIA</h2>
    <div class="carousel">
      <carousel
          v-bind="settings"
          :items-to-show="1.5"
          snapAlign="center-odd"
          :wrapAround="true"
      >
        <slide v-for="slide in images" :key="slide">
          <img :src="slide">
        </slide>

        <slide v-for="i in 1" :key="i" class="first">
          <div class="carousel__item"></div>
        </slide>

        <template #addons>
          <navigation />
          <pagination />
        </template>
      </carousel>


    </div>
  </div>

</template>

<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

export default {
  components: { Carousel, Slide, Pagination, Navigation },
  props: ['images'],
  data() {
    return {
      settings: {
        itemsToShow: 4,
        snapAlign: 'center-even',
      },
    }
  }
}
</script>

<style lang="scss" scoped>
  .gallery {
    display: flex;
    flex-direction: column;
    align-items: center;

  }
  .carousel__slide {
    padding: 5px;
    height: 60vh;
  }

  .carousel__slide--sliding {
    transition: 0.5s;
  }

  .carousel__slide {
    opacity: 0.3;
  }

  .carousel__slide--active ~ .carousel__slide {
  }

  .carousel__slide--prev {
    opacity: 1;
  }

  .carousel__slide--next {
    opacity: 1;
  }

  .carousel__slide--active {
    opacity: 1;
  }

</style>