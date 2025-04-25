<template>
  <section class="tests" id="tests">
    <h2 class="tests__title">Информатикадан тесттер</h2>
    <p class="tests__subtitle">
      Үйрен, тесттен өтіп, технологиялар әлемінде дағдыларыңды дамыт!
    </p>

    <div class="swiper-container" v-if="isMobile">
      <swiper
        :slides-per-view="2"
        :centered-slides="true"
        :space-between="20"
        :loop="true"
        :pagination="{ clickable: true }"
        :navigation="true"
        class="swiper__list"
      >
        <swiper-slide
          v-for="test in tests"
          :key="test.id"
          class="swiper__list-slide"
        >
          <TestsItem :test="test" @openTest="openTest" />
        </swiper-slide>
      </swiper>
    </div>

    <div class="container tests__list">
      <TestsItem
        v-for="test in tests"
        :key="test.id"
        :test="test"
        @openTest="openTest"
      />
    </div>
    <!-- <TestModal v-show="showModal" @closeTestModal="closeTestModal" /> -->
    <Teleport to="body">
      <div v-if="isLoading" class="loader">
        <div class="spinner"></div>
      </div>
      <component
        :is="testModal"
        v-if="showModal"
        :testUrl="selectedTestUrl"
        @closeTestModal="closeTestModal"
      />
    </Teleport>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';
import TestsItem from "@/components/TestsItem/TestsItem.vue";
// import TestModal from "@/components/TestModal/TestModal.vue";
import { ref, onMounted } from "vue";

const selectedTestUrl = ref("")
const testModal = ref(null)
const showModal = ref(false)
const isLoading = ref(false)
const isMobile = ref(false)

onMounted(() => {
  isMobile.value = window.innerWidth <= 480

  window.addEventListener('resize', () => {
    isMobile.value = window.innerWidth <= 480
  })
})

const openTest = async (test) => {
  selectedTestUrl.value = test.url
  isLoading.value = true

  if (!testModal.value) {
    const module = await import("@/components/TestModal/TestModal.vue")
    testModal.value = module.default
  }

  isLoading.value = false
  showModal.value = true
}

const closeTestModal = () => {
  showModal.value = false;
};

const tests = ref([
  {
    id: 1,
    title: "Тақырып 1: Ақпарат және оның түрлері",
    url: "https://wordwall.net/ru/embed/492576d290d84bbe9b592b27c2f14ad8?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 2,
    title: "Тақырып 2: Компьютер құрылғылары",
    url: "https://wordwall.net/ru/embed/e6a8fb67c4a54f3a83a19e48c38de7f5?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 3,
    title: "Тақырып 3: Алгоритмдер және орындаушылар",
    url: "https://wordwall.net/ru/embed/c93f9251a0aa4e048abcb4b3c65a4a45?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 4,
    title: "Тақырып 4: Интернет және қауіпсіздік ережелері",
    url: "https://wordwall.net/ru/embed/ac58c137b2b64486b2aef435d1922548?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 5,
    title: "Тақырып 5: Визуалды программалаудың негіздері(Scratch)",
    url: "https://wordwall.net/ru/embed/c83003b4e9b8438ba0fe93f3c7611974?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 6,
    title: "Тақырып 6: Операциялық жүйе және жұмыс үстелі",
    url: "https://wordwall.net/ru/embed/ad6e4085bb614077b78c790be06ea6a0?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 7,
    title: "Тақырып 7: Файлдар мен бумалармен жұмыс",
    url: "https://wordwall.net/ru/embed/f1056f93e8824711a4194030fb62da6d?themeId=64&templateId=5&fontStackId=0",
  },
  {
    id: 8,
    title: "Тақырып 8: Текстік редакторлармен жұмыс (MS Word т.б)",
    url: "https://wordwall.net/ru/embed/e3b5cace86b94e71b347b1def5164b4a?themeId=62&templateId=5&fontStackId=0",
  },
  {
    id: 9,
    title: "Тақырып 9: Графикалық редакторлар (мысалы: Paint)",
    url: "https://wordwall.net/ru/embed/1bff9fa680fd43749a97e0af5476b9bb?themeId=56&templateId=5&fontStackId=0",
  },
  {
    id: 10,
    title: "Тақырып 10: Ақпаратты сақтау және тасымалдау құрылғылары",
    url: "https://wordwall.net/ru/embed/f6a7dae9988b4ff39e190c6caded516a?themeId=50&templateId=5&fontStackId=0",
  },
  {
    id: 11,
    title: "Тақырып 11: Презентация жасау негіздері (PowerPoint)",
    url: "https://wordwall.net/ru/embed/46149acb052245f78de5a780e420522c?themeId=50&templateId=5&fontStackId=0",
  },
  {
    id: 12,
    title:
      "Тақырып 12: Желілік технологиялар және бұлтты сақтау (Google Drive т.б.)",
    url: "https://wordwall.net/ru/embed/1f1f881f67a34d76a57edcddc11cb56a?themeId=65&templateId=5&fontStackId=0",
  },
]);
</script>

<style scoped>
.loader {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100;
}

.spinner {
    border: 4px solid rgba(255, 255, 255, 0.3);
    border-top: 4px solid #3498db;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
</style>