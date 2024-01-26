<script setup >
const props = defineProps({ prices: Array });
</script>

<template>
  <div>
    <div v-for="price in props.prices" :key="price" class="cardPrice">
      <div class="label">
        {{ price.title }}
      </div>
      <div class="cardPrice__subtitle">
        {{ price.subTitle }}
      </div>
      <div v-for="description in price.descriptions" :key="description">
        <span class="cardPrice__description">
          {{ description }}
        </span>
      </div>
      <div class="cardPrice__amount">{{ price.amount }} €</div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.cardPrice {
  background-color: var(--primarySurface);
  box-shadow: 0px 4px 15px 5px #0000000d;
  padding: 1rem;

  &__subtitle {
    color: var(--tertiaryContent);
    padding: 0.8rem 0;
  }
  &__description {
    padding: 0.8rem 0;
    color: var(--primaryContent);
  }
  &__amount {
    margin-top: 0.8rem;
    background-color: var(--vert);
    width: fit-content;
    padding: 2px 8px;
  }
}
</style>