<script setup >
const props = defineProps({
  packs: Array,
});
</script>

<template>
  <div class="packs">
    <div v-for="pack in props.packs" :key="pack" class="pack">
      <span class="label">
        {{ pack.title }}
      </span>
      <span class="subTitle">
        {{ pack.subTitle }}
      </span>
      <div v-for="list in pack.lists" :key="list">
        {{ list }}
      </div>
      <span class="price">
        {{ pack.price }}
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.packs {
  margin: 1rem 0;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  .pack {
    display: flex;
    flex-direction: column;
    gap: 2px;
    border-radius: 8px;
    background: var(--primarySurface);
    box-shadow: 0px 4px 15px 5px rgba(0, 0, 0, 0.05);
    padding: 12px;

    .subTitle {
      color: var(--tertiaryContent);
    }

    .price {
      background-color: var(--vert);
      padding: 0px 8px;
      width: fit-content;
    }
  }
}
</style>