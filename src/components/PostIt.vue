
<template>
  <div id="app">
    <div
      id="box-droppable1"
      @drop="drop"
      @dragover="allowDrop"
      ref="dropZoneRef"
    >
      <div v-for="postIt in props.postIts" :key="postIt.id" class="postIts">
        <div
          @dragstart="onDragging"
          :id="postIt.id"
          draggable="true"
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
      </div>
      <div
        class="cat"
        ref="catRef"
        @dragstart="onDragging"
        draggable="true"
        id="cat"
      >
        🐭
      </div>
      <div
        class="commentaire"
        @dragstart="onDragging"
        draggable="true"
        id="commentaire"
      >
        <img src="../assets/camilleCom.svg" alt="" />
        <div class="content">
          <div class="content-header">
            <p class="label">Camille Glaçon</p>
            <small>5 min. ago</small>
          </div>
          <p class="sub-content">Et tellement plus ! Contactez-moi !</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const dropZoneRef = ref(null);
const catRef = ref(null);

const props = defineProps({ postIts: Array });

const movecat = () => {
  if (!catRef.value || !dropZoneRef.value) return;

  const boxDroppable = dropZoneRef.value;
  const catElement = catRef.value;

  const catX =
    Math.random() * (boxDroppable.clientWidth - catElement.clientWidth);
  const catY =
    Math.random() * (boxDroppable.clientHeight - catElement.clientHeight);

  const maxX = boxDroppable.clientWidth - catElement.clientWidth;
  const maxY = boxDroppable.clientHeight - catElement.clientHeight;

  catElement.style.transition = "left 1s, top 1s";
  catElement.style.left = `${Math.min(maxX, Math.max(0, catX))}px`;
  catElement.style.top = `${Math.min(maxY, Math.max(0, catY))}px`;

  // Réinitialiser la transition après le déplacement
  setTimeout(() => {
    catElement.style.transition = "";
  }, 1000);

  // Répéter le mouvement
  setTimeout(movecat, 2000);
};
// const checkCatOverElement = () => {
//   const catElement = catRef.value;
//   const dropZone = dropZoneRef.value;
//   const postItElements = dropZone
//     ? dropZone.getElementsByClassName("postIt")
//     : [];

//   // Iterate over each postIt element
//   Array.from(postItElements).forEach((postIt) => {
//     const postItRect = postIt.getBoundingClientRect();
//     const catRect = catElement.getBoundingClientRect();

//     // Check if the cat is over the postIt element
//     if (
//       catRect.left < postItRect.right &&
//       catRect.right > postItRect.left &&
//       catRect.top < postItRect.bottom &&
//       catRect.bottom > postItRect.top
//     ) {
//       // Log "miaou" when the cat is over the postIt element
//       console.log("Miaou! The cat is over the element!");

//       // Programmatically trigger the drag-and-drop operation
//       const dragEvent = new Event("dragstart", { bubbles: true });
//       catElement.dispatchEvent(dragEvent);

//       // Wait for a short time and then simulate a drop
//       setTimeout(() => {
//         const dropEvent = new Event("drop", { bubbles: true });
//         postIt.dispatchEvent(dropEvent);
//       }, 1000);
//     }
//   });
// };

onMounted(() => {
  // Démarrer le mouvement de la souris
  movecat();
  // setInterval(checkCatOverElement, 500);
});
const onDragging = (ev) => {
  console.log(ev.target.id);
  ev.dataTransfer.setData("text", ev.target.id);
};
const allowDrop = (ev) => {
  ev.preventDefault();
};

const drop = (ev) => {
  ev.preventDefault();
  const draggedElement = document.getElementById(
    ev.dataTransfer.getData("text")
  );
  // Obtenir la position de la souris par rapport à la fenêtre
  const catX = ev.clientX;
  const catY = ev.clientY;

  // Obtenir la position de la dropzone par rapport à la fenêtre
  const dropzoneRect = document
    .getElementById("box-droppable1")
    .getBoundingClientRect();
  const dropzoneX = dropzoneRect.left + window.scrollX;
  const dropzoneY = dropzoneRect.top + window.scrollY;

  // Calculer la position correcte de l'élément
  let elementLeft = catX - draggedElement.clientWidth / 2 - dropzoneX;
  let elementTop = catY - draggedElement.clientHeight / 2 - dropzoneY;

  // Assurer que l'élément reste entièrement à l'intérieur de la drop zone
  elementLeft = Math.max(
    0,
    Math.min(elementLeft, dropzoneRect.width - draggedElement.clientWidth)
  );
  elementTop = Math.max(
    0,
    Math.min(elementTop, dropzoneRect.height - draggedElement.clientHeight)
  );

  // Appliquer la nouvelle position à l'élément
  draggedElement.style.position = "absolute";
  draggedElement.style.left = `${elementLeft}px`;
  draggedElement.style.top = `${elementTop}px`;
};
</script>

<style lang="scss" scoped>
#app {
  width: 100%;
  display: flex;

  #box-droppable1 {
    width: 100%;
    min-height: 300px;
    height: 70dvh;
    position: relative;
  }
}

.postIts {
  width: fit-content;
}
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
.cat {
  position: absolute;
  font-size: 20px;
  user-select: none;
}
</style>