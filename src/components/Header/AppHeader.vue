<script setup>
import PostIt from "./PostIt.vue";
import Comment from "./Comment.vue";
import Button from "../Button.vue";
import { onMounted, ref } from "vue";
const postIts = [
  {
    text: "Je conçois des sites web, des applications et des identités graphiques",
    author: "Camille Glaçon",
    width: "320px",
    height: "230px",
    color: "--violet",
    id: 0,
    initialTop: 4,
    initialLeft: 52,
    zIndex: -2,
  },
  {
    text: "Je suis Camille Glaçon",
    author: "Camille Glaçon",
    width: "270px",
    height: "150px",
    color: "--beige",
    id: 2,
    initialTop: 5,
    initialLeft: 20,
    zIndex: -1,
  },
  {
    text: "UX/UI Designer & Brand Designer ",
    author: "Camille Glaçon",
    width: "300px",
    height: "200px",
    color: "--vert",
    id: 1,
    initialTop: 13,
    initialLeft: 34,
    zIndex: 0,
  },
];

const dropZoneRef = ref(null);
const mouseRef = ref(null);

onMounted(() => {
  moveMouse();
});

const moveMouse = () => {
  if (!mouseRef.value || !dropZoneRef) return;
  const boxDroppable = dropZoneRef.value;
  const mouseElement = mouseRef.value;

  const mouseX =
    Math.random() * (boxDroppable.clientWidth - mouseElement.clientWidth);
  const mouseY =
    Math.random() * (boxDroppable.clientHeight - mouseElement.clientHeight);

  const maxX = boxDroppable.clientWidth - mouseElement.clientWidth;
  const maxY = boxDroppable.clientHeight - mouseElement.clientHeight;

  mouseElement.style.transition = "left 1s, top 1s";
  mouseElement.style.left = `${Math.min(maxX, Math.max(0, mouseX))}px`;
  mouseElement.style.top = `${Math.min(maxY, Math.max(0, mouseY))}px`;

  // Réinitialiser la transition après le déplacement
  setTimeout(() => {
    mouseElement.style.transition = "";
  }, 1000);

  // Répéter le mouvement
  setTimeout(moveMouse, 2000);
};
</script>

<template>
  <div class="header">
    <div class="header__postIts" ref="dropZoneRef">
      <PostIt :postIt="postIt" v-for="postIt in postIts" :key="postIt.id" />
      <Comment />
      <div class="mouse" ref="mouseRef" id="mouse">🐭</div>
    </div>
    <div class="header__btn">
      <Button text="J'ai un projet" class="primary" to="/" />
      <Button text="Découvrir mes services" class="primaryOutline" to="/" />
    </div>
  </div>
</template>


<style lang="scss" scoped>
.header {
  height: 80dvh;
  display: flex;
  flex-direction: column;
  &__postIts {
    height: 70dvh;
    position: relative;
  }
  &__btn {
    display: flex;
    justify-content: center;
    gap: 1rem;
  }
  .mouse {
    position: absolute;
    font-size: 20px;
    user-select: none;
  }
}
</style>