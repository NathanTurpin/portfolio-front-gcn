<template>
  <div class="container">
    <div
      ref="myRef1"
      style="width: 100px; height: 50px; background: black"
    ></div>
    <div style="margin-left: 100px">
      <div
        ref="myRef2"
        style="
          margin-top: 100px;
          margin-left: 100px;
          width: 100px;
          height: 50px;
          background: black;
        "
      ></div>
    </div>
  </div>
</template>

<script setup>
import LeaderLine from "leader-line-new";
import { onBeforeUnmount, onMounted, ref } from "vue";

const myRef1 = ref(null);
const myRef2 = ref(null);
console.log(myRef1);
onMounted(() => {
  const drawLine = () => {
    console.log(myRef1.value);
    new LeaderLine(
      myRef1.value, // Changement ici pour inverser la direction
      LeaderLine.pointAnchor(myRef2.value),
      {
        path: "fluid",
        startSocket: "bottom",
        endSocket: "left",
        color: "black",
        size: 2,
      }
    );
  };

  const timer = setInterval(() => {
    // if (myRef2.value) {
    clearInterval(timer);
    drawLine();
    // }
  }, 5);

  onBeforeUnmount(() => {
    clearInterval(timer);
  });
});
</script>

<style scoped>
.container {
  display: flex;
}
</style>
