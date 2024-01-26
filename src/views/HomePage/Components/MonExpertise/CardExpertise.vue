<script setup >
const props = defineProps({
  title: String,
  subTitle: { type: String, required: false },
  active: Boolean,
  contents: { type: Array },
});

import { onMounted, ref } from "vue";

onMounted(() => {});
</script>

<template>
  <div class="card">
    <div class="cardExpertise" :class="props.active ? 'active' : ''">
      <span class="label">
        {{ props.title }}
      </span>
      <div v-if="props.subTitle" class="cardExpertise__subTitle">
        {{ props.subTitle }}
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  cursor: pointer;

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
    gap: 15px;
    &__subTitle {
      border: 1px solid;
      border-radius: 0.2rem;
      padding: 0px 8px;
    }
  }

  .active {
    background-color: var(--primaryContent);
    color: var(--primarySurface);

    .label {
      color: var(--primarySurface);
    }
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