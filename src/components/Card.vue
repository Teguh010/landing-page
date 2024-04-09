<template>
  <div>
    <div>
      <transition appear enter-active-class="fadeinup ">
        <div
          v-show="isActive"
          class="text-center"
          style="position: absolute; top: -60px; right: 30%; z-index: 999"
        >
          <img style="width: 150px" src="src/assets/tooltip2.png" />
        </div>
      </transition>
    </div>
    <q-card class="my-card" flat :class="{ 'active-card': isActive }">
      <q-card-section>
        <div class="flex justify-center">
          <div class="image-avatar-container">
            <q-avatar size="120px">
              <img style="width: 120px" src="src/assets/example-photo.png" />
            </q-avatar>
            <img
              style="width: 20px"
              class="image-badge"
              src="src/assets/country-flag.png"
            />
          </div>
        </div>
      </q-card-section>

      <q-card-section>
        <div class="card-main-title">Abhishek Gupta {{ isActive }}</div>
        <div class="card-second-title">마케팅 · 2y+</div>
      </q-card-section>

      <q-card-section class="q-pt-none">
        <div class="flex justify-center">
          <q-chip outline color="accent" text-color="white">
            <span class="card-content-text"> 마케팅 콘텐츠 제작 </span>
          </q-chip>
          <q-chip outline color="accent" text-color="white">
            <span class="card-content-text"> 인스타그램 관리 </span>
          </q-chip>
          <q-chip outline color="accent" text-color="white">
            <span class="card-content-text"> 트위터 관리 </span>
          </q-chip>
          <q-chip outline color="accent" text-color="white">
            <span class="card-content-text"> 블로그 글 작성 </span>
          </q-chip>
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>
<script>
export default {
  name: 'UserCard',
  props: {
    isActive: Boolean,
  },
};
</script>
<style scoped>
.image-avatar-container {
  position: relative;
}
.image-badge {
  position: absolute;
  right: 2px;
  bottom: 15px;
}
.card-main-title {
  text-align: center;
  font-weight: 900;
  font-size: 24px;
  line-height: 36px;
  color: linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2));
}
.card-second-title {
  text-align: center;
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
.my-card {
  width: 292px;
  border-radius: 8px;
}
.active-card {
  box-shadow: 0px 15px 24px 0px rgba(0, 0, 0, 0.12) !important;
}
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
</style>
