<template>
  <q-layout view="hhh lpR fff">
    <q-header
      :class="$q.platform.is.desktop ? 'q-py-md q-px-xl' : 'q-py-sm'"
      class="bg-transparent"
    >
      <q-toolbar>
        <q-toolbar-title>
          <div>
            <img style="width: 150px" src="src/assets/HipeHireLogo.png" />
          </div>
        </q-toolbar-title>

        <q-space v-if="!$q.platform.is.mobile" />
        <div v-if="!$q.platform.is.mobile">
          <q-btn color="white" flat icon-right="expand_more">
            <span class="header-label"> {{ selectedMenu.label }}</span>
            <q-menu>
              <q-list style="min-width: 100px">
                <q-item
                  v-for="(item, index) in menuItems"
                  :key="index"
                  clickable
                  v-close-popup
                  @click="updateSelectedMenu(item)"
                >
                  <q-item-section
                    :class="
                      selectedMenu.label === item.label ? 'text-bold' : ''
                    "
                    >{{ item.label }}</q-item-section
                  >
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
        </div>
        <div v-if="!$q.platform.is.mobile" class="q-pl-xl">
          <span class="header-label"> 해외 개발자 활용 서비스 </span>
        </div>
        <q-space v-if="!$q.platform.is.mobile" />
        <div v-if="!$q.platform.is.mobile">
          <q-btn
            style="border-radius: 8px"
            class="bg-white text-primary no-box-shadow text-bold"
            label="문의하기"
            flat
          />
        </div>
      </q-toolbar>
    </q-header>
    <q-footer style="background: #fbfbfb">
      <FooterContent />
    </q-footer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import FooterContent from 'src/components/FooterContent.vue';
import { ref } from 'vue';

const menuItems = ref([
  { label: '채용', color: 'primary' },
  { label: '해외 개발자 원격 채용', color: 'secondary' },
  { label: '외국인 원격 채용 (비개발 직군)', color: 'primary' },
  { label: '한국어 가능 외국인 채용', color: 'secondary' },
]);

const selectedMenu = ref(menuItems.value[0]); // Default adalah item pertama

function updateSelectedMenu(item) {
  selectedMenu.value = item;
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
body {
  font-family: 'Poppins', sans-serif !important;
  background: linear-gradient(151.17deg, #26c2b9 8.69%, #288be7 126.06%);
  /* background-image: url('/src/assets/bg-quasar-project.png'); */
  /* background-blend-mode: color-burn; */
}
.header-label {
  font-weight: 900;
  font-size: 16px;
  line-height: 24px;
  color: #ffffff;
}

@media (max-width: 768px) {
  body {
    font-family: 'Poppins', sans-serif !important;
    background: linear-gradient(151.17deg, #26C2B9 8.69%, #288BE7 126.06%);
  }
}
</style>
