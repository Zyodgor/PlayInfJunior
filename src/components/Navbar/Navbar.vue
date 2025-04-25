<template>
  <nav class="nav">
    <div class="container nav__content">
        <router-link class="nav__content-logo" to="/">
            <img src="@/assets/images/logo.png" alt="">
            <span>PlayInfJunior</span>
        </router-link>
        <button class="nav__content-menu" @click="burger = true">
          <img src="@/assets/images/menu.svg" alt="">
        </button>
        <ul :class="['nav__content-list', {'active': burger}]">
            <router-link class="nav__content-logo" to="/" @click="burger = false">
              <img src="@/assets/images/logo.png" alt="">
              <span>PlayInfJunior</span>
            </router-link>
            <li><router-link @click="burger = false" :to="{hash: '#why'}" class="nav__content-link">Неге ойындар?</router-link></li>
            <li><router-link @click="burger = false" :to="{hash: '#tests'}" class="nav__content-link">Тесттер</router-link></li>
            <li><router-link @click="burger = false" :to="{hash: '#games'}" class="nav__content-link">Ойындар</router-link></li>
            <button class="nav__content-close" @click="burger = close" v-show="burger">
              <img src="@/assets/images/x-mark.png" alt="">
            </button>
        </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

const burger = ref(false);
</script>