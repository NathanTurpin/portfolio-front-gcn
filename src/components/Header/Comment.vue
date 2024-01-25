<script setup >
import draggable from "../../directives/draggable";
const vDraggable = draggable;
</script>

<template>
  <div class="commentaire" id="commentaire" v-draggable>
    <img src="../../assets/camilleCom.svg" alt="" />
    <div class="content">
      <div class="content-header">
        <p class="label">Camille Glaçon</p>
        <small>5 min. ago</small>
      </div>
      <p class="sub-content">Et tellement plus ! Contactez-moi !</p>
    </div>
  </div>
  ;
</template>

<style lang="scss" scoped>
.commentaire {
  cursor: grab;

  z-index: 1;
  position: absolute;
  display: flex;
  align-items: center;
  gap: 10px;
  box-shadow: 0px 4px 15px 0px #0000000d;
  width: fit-content;
  padding: 14px;
  border-radius: 20px 20px 20px 0px;
  top: 18rem;
  background-color: var(--secondarySurface);
  left: 54rem;
  .content {
    display: flex;
    flex-direction: column;
    .content-header {
      display: flex;
      justify-content: space-between;

      p {
        color: var(--primaryContent);
        font-weight: bold;
      }
      small {
        color: #00000066;
      }
    }

    .sub-content {
      color: var(--secondaryContent);
    }
  }
}
</style>