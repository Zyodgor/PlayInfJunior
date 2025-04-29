<template>
  <section class="games" id="games">
    <div class="container games__cards">
      <GameCard 
        v-for="game in games"
        :key="game.id"
        :game="game"
        @openGame="openGame"
      />
    </div>
    <Teleport to="body">
      <div v-if="isLoading" class="loader">
        <div class="spinner"></div>
      </div>
      <component
        :is="gameModal"
        v-if="showModal"
        :gameUrl="selectedGameUrl"
        @closeGameModal="closeGameModal"
      />
    </Teleport>
  </section>
</template>

<script setup>
import GameCard from "@/components/GameCard/GameCard.vue";
import firstGameImg from "@/assets/images/game1.png"
import secondGameImg from "@/assets/images/game2.png"
import anagramma from "@/assets/images/anagramma.png"
import { ref, onMounted } from "vue";

const selectedGameUrl = ref("")
const gameModal = ref(null)
const showModal = ref(false)
const isLoading = ref(false)
const isMobile = ref(false)

onMounted(() => {
  isMobile.value = window.innerWidth <= 480

  window.addEventListener('resize', () => {
    isMobile.value = window.innerWidth <= 480
  })
})

const openGame = async (game) => {
    selectedGameUrl.value = game.url
  isLoading.value = true

  if (!gameModal.value) {
    const module = await import("@/components/GameModal/GameModal.vue")
    gameModal.value = module.default
  }

  isLoading.value = false
  showModal.value = true
}

const closeGameModal = () => {
  showModal.value = false;
}

const games = ref([
  {
    id: 1,
    name: "Анаграмма: Компьютерлік терминдерді шешіп ал!",
    img: anagramma,
    url: "https://wordwall.net/ru/embed/e08b44d8264e4cd584858c3c6bac1d05?themeId=23&templateId=38&fontStackId=0"
  },
  {
    id: 2,
    name: "Көртышқанды ұр!: Ақпарат тасымалдаушы құралдар (Носители информации)",
    img: firstGameImg,
    url: "https://wordwall.net/ru/embed/62fb1923d2ce40b7808ba08e16de769e?themeId=23&templateId=45&fontStackId=0"
  },
  {
    id: 3,
    name: "Көртышқанды ұр!: Программалар түрлері (Типы программ)",
    img: secondGameImg,
    url: "https://wordwall.net/ru/embed/7e8f7c536d4d46eba99632d2b8e0f1b4?themeId=22&templateId=45&fontStackId=0"
  },
])


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