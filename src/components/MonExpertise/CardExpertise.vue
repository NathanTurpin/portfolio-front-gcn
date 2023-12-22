<script setup >
const props = defineProps({
  title: String,
  subTitle: { type: String, required: false },
  active: Boolean,
});
</script>

<template>
  <div class="cardExpertise" :class="props.active ? 'active' : ''">
    <span class="label">
      {{ props.title }}
    </span>
    <div v-if="props.subTitle" class="cardExpertise__subTitle">
      {{ props.subTitle }}
    </div>
  </div>
</template>

<style lang="scss" scoped>
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
</style>