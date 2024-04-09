<template>
  <div class="swiper-container">
    <swiper
    ref="mySwiper"
      :loop="true"
      :effect="'coverflow'"
      :grabCursor="true"
      :centeredSlides="true"
      :slidesPerView="'auto'"
      :coverflowEffect="{
        rotate: 0,
        stretch: 150,
        depth: 100,
        modifier: 1,
        slideShadows: false,
      }"
      :navigation="true"
      :modules="modules"
      @activeIndexChange="handleActiveIndexChange"
      class="mySwiper"
    >
      <swiper-slide v-for="(card, index) in cards" :key="index">
        <div>index: {{ index }} active index: {{ activeIndex }}</div>
        <Card :isActive="index  === activeIndex" />
      </swiper-slide>
    </swiper>
  </div>
</template>
<script>
import Card from 'src/components/Card.vue';
import { Swiper, SwiperSlide } from 'swiper/vue';

import 'swiper/css';

import 'swiper/css/effect-coverflow';
import 'swiper/css/navigation';

import { EffectCoverflow, Navigation } from 'swiper/modules';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Card,
  },
  setup() {
    return {
      modules: [EffectCoverflow, Navigation],
      activeIndex: 0, 
      cards: Array.from({ length: 5 }, (_, index) => index), 
    };
  },
  methods: {
    handleActiveIndexChange(newIndex) {
      this.activeIndex = newIndex.realIndex;

    }
  },
    mounted() {
      this.$nextTick(() => {
                    console.log('newIndex', this.$refs.mySwiper)

    // Coba akses Swiper di sini
  });

    setTimeout(() => {
      if (this.$refs.mySwiper && this.$refs.mySwiper.swiper) {
        this.$refs.mySwiper.swiper.slideNext();
        // Misal, setelah slideNext, Anda ingin memperbarui index berdasarkan kondisi tertentu
      }
    }, 2000);
  }
};
</script>
<style scoped>
.swiper-container {
  width: 554px;
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
</style>
