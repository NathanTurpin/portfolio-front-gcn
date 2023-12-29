<script setup>
import PostIt from "./PostIt.vue";
import Button from "./Button.vue";
const postIts = [
  {
    text: "Je conçois des sites web, des applications et des identités graphiques",
    author: "Camille Glaçon",
    width: "420px",
    height: "330px",
    color: "--violet",
    id: 0,
    initialTop: 4,
    initialLeft: 52,
    zIndex: -2,
  },
  {
    text: "Je suis Camille Glaçon",
    author: "Camille Glaçon",
    width: "370px",
    height: "250px",
    color: "--beige",
    id: 2,
    initialTop: 5,
    initialLeft: 20,
    zIndex: -1,
  },
  {
    text: "UX/UI Designer & Brand Designer ",
    author: "Camille Glaçon",
    width: "400px",
    height: "200px",
    color: "--vert",
    id: 1,
    initialTop: 13,
    initialLeft: 34,
    zIndex: 0,
  },
];
</script>

<template>
  <div class="header">
    <PostIt :postIts="postIts" />
    <div class="header__btn">
      <Button text="J'ai un projet" class="primary" to="/" />
      <Button text="Découvrir mes services" class="primaryOutline" to="/" />
    </div>
  </div>
</template>


<style lang="scss" scoped>
.header {
  height: 80dvh;
  position: relative;

  &__btn {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
}
</style>