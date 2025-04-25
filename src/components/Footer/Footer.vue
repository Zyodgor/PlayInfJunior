<template>
  <footer class="footer">
    <div class="container footer__content">
      <router-link :to="{ hash: '/' }" class="footer__logo">
        <img src="@/assets/images/logo.png" alt="" />
        <span>PlayInfJunior</span>
      </router-link>
      <ul class="footer__list">
        <li><a href="" class="footer__link">Неге ойындар?</a></li>
        <li><a href="" class="footer__link">Тесттер</a></li>
        <li><a href="" class="footer__link">Ойындар</a></li>
      </ul>
      <div class="footer__icons">
        <a target="_blank" href="https://t.me/tukhtabaevaa">
          <img src="@/assets/images/telegram.svg" alt="" />
        </a>
        <a
          target="_blank"
          href="https://www.instagram.com/tukhtabaeva_zh/?utm_source=ig_web_button_share_sheet"
        >
          <img src="@/assets/images/instagram.svg" alt="" />
        </a>
      </div>
    </div>
    <div class="footer__end">
      <p>© 2025 PlayInfJunior. Все права защищены.</p>
    </div>
  </footer>
</template>

<script setup>
</script>