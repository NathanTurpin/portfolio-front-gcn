<script setup >
import Button from "../Button.vue";
</script>

<template>
  <nav class="navbar">
    <img src="../../assets/logo.svg" alt="logo" class="navbar__img" />
    <div class="navbar__link">
      <router-link to="">Mes services</router-link>
      <router-link to="">Projets</router-link>
      <router-link to="">Ma démarche</router-link>
      <Button to="/" class="primary" text="J'ai un projet" />
    </div>
  </nav>
</template>

<style lang="scss" scoped>
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem;

  &__img {
    width: 100px;
  }

  &__link {
    display: flex;
    align-items: center;
    gap: 2rem;
  }
}
</style>