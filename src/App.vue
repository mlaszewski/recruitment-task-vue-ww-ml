<template>

  <NavBar :contact-modal-handler="toggleContactModal"/>
  <div class="section hero" id="start">
    <img src="/images/reinhart-julian-WxM465oM4j4-unsplash.png" alt="hero image" />
  </div>
  <AboutMe />
  <GalleryCarousel :images="carouselImages" />

  <ContactModal v-if="isContactModalActive" :close-handler="toggleContactModal" />

  <footer class="footer"></footer>

</template>

<script>
import NavBar from "@/components/NavBar.vue";
import AboutMe from "@/components/AboutMe.vue";
import GalleryCarousel from "@/components/GalleryCarousel.vue";
import ContactModal from "@/components/ContactModal.vue";

export default ({
  components: {
    NavBar,
    AboutMe,
    GalleryCarousel,
    ContactModal
  },
  data() {
    return {
      isContactModalActive: false,
      carouselImages: [
        "/images/reinhart-julian-_r0lZDocH78-unsplash.png",
        "/images/reinhart-julian-H4AejIh_l7g-unsplash.png",
        "/images/reinhart-julian-S9BOTsGr2ww-unsplash.png",
        "/images/reinhart-julian-VnI_piHNlok-unsplash.png",
      ]
    }
  },
  methods: {
    toggleContactModal () {
      this.isContactModalActive = !this.isContactModalActive;
    }
  }
})
</script>

<style lang="scss">

// initials
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Montserrat;
  font-size: 13px;
  line-height: 1.25em;
}

html {
  scroll-behavior: smooth;
}

body {
  overflow-x: hidden;
}

img {
  width: 100%;
}

.section {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.section-header {
  font-family: Montserrat;
  font-weight: 900;
  font-size: 3em;
  border-bottom: 2px solid $color-accent;
  padding: .5em 0;
  margin: .5em 0;
  letter-spacing: .2em;
}

.hero {
  height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;

  img {
    position: relative;
    top: 90px;
  }

  @media (max-width: $medium) {
    height: 70vh;
    img {
      height: 100%;
      width: auto;
    }
  }
}

.footer {
  margin-top: 4em;
  background: $color-secondary;
  height: 200px;
}

</style>
