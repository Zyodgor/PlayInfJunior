<template>
  <div class="tests__item">
    <h3 class="tests__item-title">{{ test.title }}</h3>
    <a class="tests__item-link" @click="openTest(test)">Тесті тапсыру</a>
  </div>
</template>

<script setup>
import { defineProps } from "vue"

const emit = defineEmits();

const openTest = (test) => {
    emit('openTest', test)
}

const props = defineProps({
    test: Object
})
</script>