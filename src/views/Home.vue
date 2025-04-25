<template>
  <Navbar />
  <Header />
  <main class="main">
    <Why />
    <Tests />
    <Games />
  </main>
  <Footer/>
</template>

<script setup>
import Navbar from "@/components/Navbar/Navbar.vue";
import Header from "@/components/Header/Header.vue";
import Why from "@/components/Why/Why.vue";
import Tests from "@/components/Tests/Tests.vue";
import Games from "@/components/Games/Games.vue";
import Footer from "@/components/Footer/Footer.vue";
</script>
