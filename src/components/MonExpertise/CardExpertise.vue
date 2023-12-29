<script setup >
const props = defineProps({
  title: String,
  subTitle: { type: String, required: false },
  active: Boolean,
  references: { type: Array, required: false },
});

import LeaderLine from "leader-line-new";
import { onBeforeUnmount, onMounted, ref } from "vue";
const itemRefs = ref([]);
const skipUnwrap = { itemRefs };
const myRef1 = ref(props.references[0]);
const myRef2 = ref(props.references[1]);

onMounted(() => {
  console.log(itemRefs.value.map((i) => i.textContent));
  const drawLine = () => {
    console.log(itemRefs.value.map((i) => i.textContent));
    console.log(myRef1.value);
    if (props.references[1] !== undefined) {
      new LeaderLine(
        props.references[0], // Changement ici pour inverser la direction
        LeaderLine.pointAnchor(props.references[1]),
        {
          path: "fluid",
          startSocket: "bottom",
          endSocket: "left",
          color: "black",
          size: 2,
        }
      );
    }
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

<template>
  <div class="card">
    <div
      class="cardExpertise"
      :class="props.active ? 'active' : ''"
      :ref="skipUnwrap.itemRefs"
    >
      <span class="label">
        {{ props.title }}
      </span>
      <div v-if="props.subTitle" class="cardExpertise__subTitle">
        {{ props.subTitle }}
      </div>
    </div>

    <div
      class="rond"
      v-if="props.references.length > 1"
      :ref="props.references[1]"
    >
      <img src="../../assets/Plus.svg" alt="" />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;

  .cardExpertise {
    width: fit-content;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    background-color: var(--primarySurface);
    color: var(--secondaryContent);
    border-radius: 0.5rem;
    box-shadow: 0px 4px 15px 5px #0000000d;

    &__subTitle {
      border: 1px solid;
      border-radius: 0.2rem;
      padding: 0px 8px;
    }
  }

  .active {
    color: var(--primarySurface);
    background-color: var(--primaryContent);
  }

  .rond {
    display: flex;
    justify-content: center;
    width: 50px;
    height: 50px;
    background-color: violet;
    border-radius: 50%;
  }
}
</style>