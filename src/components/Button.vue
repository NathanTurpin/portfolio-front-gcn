<script setup >
const props = defineProps({
  text: String,
  class: String,
  to: String,
});
</script>

<template>
  <router-link :to="props.to" :class="props.class">
    {{ props.text }}
  </router-link>
</template>

<style lang="scss" scoped>
a {
  padding: 0.5rem;
  border-radius: 5px;
}
.primary {
  background-color: var(--primaryContent);
  color: var(--secondarySurface);
}

.primaryOutline {
  color: var(--primaryContent);
  background-color: white;
  border: solid 1px var(--primaryContent);
}
</style>