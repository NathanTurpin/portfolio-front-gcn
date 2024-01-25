
<template>
  <div
    v-draggable
    :id="postIt.id"
    :style="{
      width: postIt.width,
      height: postIt.height,
      backgroundColor: `var(${postIt.color})`,
      position: 'absolute',
      top: `${postIt.initialTop}rem`, // Ajout de la position top
      left: `${postIt.initialLeft}rem`,
    }"
    class="postIt"
  >
    <b>
      {{ postIt.text }}
    </b>

    <small>{{ postIt.author }}</small>
  </div>
</template>

<script setup>
import draggable from "../../directives/draggable";
const props = defineProps({ postIt: Object });
const vDraggable = draggable;
</script>

<style lang="scss" scoped>
.postIt {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1rem;
  box-shadow: 0px 4px 15px 0px #0000000d;
  cursor: grab;
  b {
    font-size: 30px;
  }
  small {
    color: #00000066;
  }
}
</style>