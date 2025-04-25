<template>
  <div class="modal" @click="closeTestModal">
    <div class="modal__block" @click.stop>
      <div class="modal__block-responsive">
        <iframe
          :src="testUrl"
          frameborder="0"
          allowfullscreen
        ></iframe>
      </div>
      <button class="modal__block-close" @click="closeTestModal">Закрыть</button>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits();
const closeTestModal = () => {
  emit("closeTestModal");
};

const props = defineProps({
    testUrl: String
})

</script>
