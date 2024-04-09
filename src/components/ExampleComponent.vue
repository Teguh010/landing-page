<template>
  <div class="background-image">
    <div class="home-container q-pt-xl">
      <div
        class="row"
        :class="
          $q.platform.is.desktop ? ' top-container' : ' top-container-mobile'
        "
      >
        <div class="col-7 col-md-7 col-xs-12">
          <div class="row">
            <div class="col-md-9">
              <div>
                <transition-group appear enter-active-class="fadeinup ">
                  <div class="tooltip1-container" v-if="showTooltip">
                   <div>
                        <img
                          style="width: 100px"
                          src="src/assets/tooltip1.png"
                        />
                      </div>
                  </div>
                  <div class="main-title q-pb-md fadeinup-500">
                    최고의 실력을 가진 외국인 인재를 찾고 계신가요?
                  </div>
                </transition-group>
              </div>
              <div>
                <transition appear enter-active-class="fadeinup ">
                  <div class="second-title q-py-md fadeinup-500">
                    법률 및 인사관리 부담없이 1주일 이내에 원격으로
                    채용해보세요.
                  </div>
                </transition>
              </div>
              <div v-if="$q.platform.is.desktop" class="third-title q-py-md">
                개발자가 필요하신가요?
              </div>

              <div v-if="$q.platform.is.desktop">
                <transition appear enter-active-class="fadeinatonce ">
                  <div
                    class="flex hero-cards-container q-py-md fadein-atonce-500"
                  >
                    <q-card class="hero-card" flat>
                      <q-card-section>
                        <div class="third-title">평균 월 120만원</div>
                        <div class="forth-title">
                          임금을 해당 국가를 기준으로 계산합니다.
                        </div>
                      </q-card-section>
                    </q-card>
                    <q-card class="hero-card" flat>
                      <q-card-section>
                        <div class="third-title">평균 월 120만원</div>
                        <div class="forth-title">
                          임금을 해당 국가를 기준으로 계산합니다.
                        </div>
                      </q-card-section>
                    </q-card>
                    <q-card class="hero-card" flat>
                      <q-card-section>
                        <div class="third-title">평균 월 120만원</div>
                        <div class="forth-title">
                          임금을 해당 국가를 기준으로 계산합니다.
                        </div>
                      </q-card-section>
                    </q-card>
                  </div>
                </transition>
              </div>
            </div>
          </div>
        </div>
        <div
          :class="$q.platform.is.desktop ? ' col  flex justify-end' : 'col-12'"
        >
          <CoverflowSlider />
        </div>
      </div>
      <div v-if="$q.platform.is.desktop">
        <transition appear enter-active-class="fadeinx">
          <div class="slider-hero-small fadein-500">
            <GeneralSlider />
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import CoverflowSlider from 'src/components/CoverflowSwiper.vue';
import GeneralSlider from 'src/components/GeneralSwiper.vue';

export default {
  components: {
    CoverflowSlider,
    GeneralSlider,
  },
  setup() {
    const showTooltip = ref(false);
    const showMainTitle = ref(true);
    const slide = ref(1);

    // Menggunakan onMounted untuk lifecycle hook
    onMounted(() => {
      setTimeout(() => {
        showTooltip.value = true;
      }, 300);
    });

    return {
      showTooltip,
      showMainTitle,
      slide,
    };
  },
};
</script>

<style>
.home-container {
  padding: 100px 20px 0px 20px;
}
.background-image {
  /* background-image: url('/src/assets/bg-quasar-project.png');
  mix-blend-mode: color-burn; */

  /* background: linear-gradient(151.17deg, #26c2b9 8.69%, #288be7 126.06%); */
  width: 100%;
}

/* Style untuk teks */
.background-image h1 {
  color: white;
  font-size: 2rem;
}
.main-title {
  font-weight: 900;
  font-size: 48px;
  line-height: 62.4px;
  color: white;
}
.second-title {
  font-weight: 900;
  font-size: 24px;
  line-height: 34px;
  color: rgba(255, 255, 255, 0.9);
}
.third-title {
  font-weight: 900;
  font-size: 18px;
  line-height: 27px;
  color: rgba(255, 255, 255, 1);
}
.hero-card {
  background: transparent !important;
  width: 170px !important;
}
.forth-title {
  font-weight: 900;
  font-size: 16px;
  line-height: 24px;
  color: rgba(255, 255, 255, 0.8);
}
.top-container {
  padding: 0 40px;
}

/* animation */

.fadeinup {
  animation: fadeinup-animation 500ms ease-out;
}

@keyframes fadeinup-animation {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fadeinatonce {
  animation: fadein-atonce 500ms ease-out forwards;
}

@keyframes fadein-atonce {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0); /* Kembali ke posisi asli */
  }
}

.fadeinx {
  animation: fadeinx 500ms ease-out forwards;
}

@keyframes fadeinx {
  from {
    opacity: 0;
    transform: translateX(-40px);
  }
  to {
    opacity: 1;
    transform: translateY(0); /* Kembali ke posisi asli */
  }
}
</style>
