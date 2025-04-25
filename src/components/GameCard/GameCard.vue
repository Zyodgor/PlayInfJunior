<template>
  <div class="games__card">
    <div class="games__card-info">
      <div class="games__card-img">
        <img :src="game.img" alt="" />
        <a class="games__card-link" @click="openGame(game)">Ойнау</a>
      </div>
      <h3 class="games__card-title">{{ game.name }}</h3>
    </div>
    <a class="games__card-linkMobile" @click="openGame(game)">Ойнау</a>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  game: {
    typeof: Object,
    require: true,
  },
});

const emit = defineEmits();

const openGame = (game) => {
  emit("openGame", game);
};
</script>