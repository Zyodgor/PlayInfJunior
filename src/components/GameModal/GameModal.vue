<template>
  <div class="modal" @click="closeGameModal">
    <div class="modal__block" @click.stop>
      <div class="modal__block-responsive">
        <iframe :src="gameUrl" frameborder="0" allowfullscreen></iframe>
      </div>
      <button class="modal__block-close" @click="closeGameModal">
        Закрыть
      </button>
    </div>
  </div>
</template>
  
  <script setup>
const emit = defineEmits();
const closeGameModal = () => {
  emit("closeGameModal");
};

const props = defineProps({
  gameUrl: String,
});
</script>
  