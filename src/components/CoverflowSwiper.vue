<template>
  <div :class="$q.platform.is.desktop ? ' swiper-page' : ' swiper-page-mobile'">
    <div
      :class="
        $q.platform.is.desktop ? ' swiper-conent' : ' swiper-conent-mobile'
      "
    >
     
      <div class="swiper-container" ref="mySwiperContainer">
        <div class="swiper-wrapper" v-if="$q.platform.is.desktop">
          <div class="swiper-slide" v-for="(card, index) in cards" :key="index">
            <Card :isActive="index === activeIndex" />
          </div>
        </div>
        <div v-else class="swiper-wrapper">
          <div class="swiper-slide" v-for="(card, index) in cards" :key="index">
            <Card :isActive="index === activeIndex" />
          </div>
        </div>
      </div>
    </div>
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>
  </div>
</template>

<script>
import Card from 'src/components/Card.vue';

import 'swiper/css/effect-coverflow';

import Swiper from 'swiper';
import {
  Navigation,
  Pagination,
  EffectCoverflow,
  Autoplay,
} from 'swiper/modules';

import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

export default {
  components: {
    Card,
  },
  data() {
    return {
      swiperInstance: null,
      activeIndex: 0,
      activeCard: 0,
      cards: Array.from({ length: 5 }, (_, index) => index),
    };
  },
  methods: {
    handleActiveIndexChange(newIndex) {
      console.log(newIndex.realIndex);
      this.activeIndex = newIndex.realIndex;
      this.activeCard = newIndex.realIndex;
    },
  },
  computed: {
    // swiperOptions() {
    //   // Cek platform pengguna
    //   const isDesktop = this.$q.platform.is.desktop;
    //   return {
    //     modules: [Navigation, Pagination, EffectCoverflow, Autoplay],
    //     loop: true,
    //     effect: 'coverflow',
    //     grabCursor: true,
    //     centeredSlides: true,
    //     slidesPerView: 'auto',
    //     // autoplay: {
    //     //   delay: 5000,
    //     // },
    //     // spaceBetween: isDesktop ? 0 : 0,
    //     coverflowEffect: {
    //       rotate: 0,
    //       stretch: 150,
    //       depth: isDesktop ? 100 : 100,
    //       modifier: 1,
    //       slideShadows: false,
    //     },
    //     navigation: {
    //       nextEl: '.swiper-button-next',
    //       prevEl: '.swiper-button-prev',
    //     },
    //   };
    // },
  },
  mounted() {
    this.$nextTick(() => {
      // this.swiperInstance = new Swiper(
      //   this.$refs.mySwiperContainer,
      //   this.swiperOptions
      // );

      this.swiperInstance = new Swiper(this.$refs.mySwiperContainer, {
        modules: [Navigation, Pagination, EffectCoverflow, Autoplay],
        loop: true,
        effect: 'coverflow',
        grabCursor: true,
        centeredSlides: true,
        slidesPerView: 'auto',
        // autoplay: {
        //   delay: 5000,
        // },
        coverflowEffect: {
          rotate: 0,
          stretch: 150,
          depth: 100,
          modifier: 1,
          slideShadows: false,
        },
        // spaceBetween: -200,
        //  coverflowEffect: {
        //   rotate: 0,
        //   stretch: 150,
        //   depth: 300,
        //   modifier: 1,
        //   slideShadows: false,
        // },
        navigation: true,
        on: {
          activeIndexChange: this.handleActiveIndexChange,
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },
      });

      // Pindah ke slide berikutnya setelah 2 detik
      setTimeout(() => {
        this.swiperInstance.slideNext();
      }, 300);
    });
  },
  beforeUnmount() {
    // Bersihkan instance Swiper untuk mencegah kebocoran memori
    if (this.swiperInstance) {
      this.swiperInstance.destroy();
    }
  },
};
</script>

<style scoped>
.swiper-page {
  width: 600px;
  position: relative;
    margin-top: -50px

}
.swiper-page-mobile {
  width: 350px;
  position: relative;
}
.swiper-conent {
  width: 554px;
  overflow: hidden;
  position: relative;
  padding-top: 70px;

}

.swiper-conent-mobile {
  width: 340px;
  overflow: hidden;
}

.swiper {
  width: 100%;
  padding-top: 50px;
  padding-bottom: 50px;
}

.swiper-slide {
  background-position: center;
  background-size: cover;
  width: 300px;
  height: 500px;
}

/* .swiper-slide-active {
  width: 320px;
} */

.swiper-slide img {
  display: block;
  width: 100%;
}
.image-avatar-container {
  position: relative;
}
.image-badge {
  position: absolute;
  right: 2px;
  bottom: 15px;
}
.card-main-title {
  font-weight: 900;
  font-size: 24px;
  line-height: 36px;
  color: linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2));
}
.card-second-title {
  font-weight: 900;
  font-size: 16px;
  line-height: 24px;
  color: #4a77ff;
}
.card-content-text {
  font-weight: 900;
  font-size: 16px;
  line-height: 24px;
  color: #5e626f;
}

.q-chip {
  border-radius: 6px !important;
  padding: 4px 10px !important;
}

.swiper-button-prev,
.swiper-rtl .swiper-button-next {
  /* padding-right: 40px; */
  left: unset !important;
  right: auto;
  margin-left: -50px;
  top: 40% !important;
}
.swiper-button-next,
.swiper-rtl .swiper-button-prev {
  right: 1.5% !important;
  left: auto;
  top: 40% !important;
}

.swiper-button-prev:after,
.swiper-button-next:after {
  font-family: swiper-icons;
  font-size: 30px !important;
  font-weight: 900 !important;
  text-transform: none !important;
  letter-spacing: 0;
  font-variant: initial;
  line-height: 1;
  color: white;
}

@media (max-width: 768px) {
  .swiper-button-prev,
  .swiper-rtl .swiper-button-next {
    left: unset !important;
    right: auto;
    margin-left: -10px;
    top: 40% !important;
  }
  .swiper-button-next,
  .swiper-rtl .swiper-button-prev {
    right: 1.5% !important;
    left: auto;
    top: 40% !important;
  }

  .swiper-button-prev:after,
  .swiper-button-next:after {
    font-family: swiper-icons;
    font-size: 30px !important;
    font-weight: 900 !important;
    text-transform: none !important;
    letter-spacing: 0;
    font-variant: initial;
    line-height: 1;
    color: white;
  }
}
</style>
