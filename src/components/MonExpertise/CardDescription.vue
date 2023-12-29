<script setup >
const props = defineProps({
  descriptions: Array,
});

const closeDescription = (description) => {
  description.closed = !description.closed;
};
</script>

<template>
  <div>
    <div
      v-for="description in props.descriptions"
      :key="description.title"
      class="description"
    >
      <div class="description-header">
        <span class="label">
          {{ description.title }}
        </span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="21"
          viewBox="0 0 20 21"
          fill="none"
          class="close"
          @click="closeDescription(description)"
        >
          <path
            fill-rule="evenodd"
            clip-rule="evenodd"
            d="M5.05131 5.55025C5.23885 5.36272 5.4932 5.25736 5.75842 5.25736C6.02363 5.25736 6.27799 5.36272 6.46552 5.55025L10.0011 9.08579L13.5366 5.55025C13.7241 5.36272 13.9785 5.25736 14.2437 5.25736C14.5089 5.25736 14.7633 5.36272 14.9508 5.55025C15.1383 5.73779 15.2437 5.99214 15.2437 6.25736C15.2437 6.52258 15.1383 6.77693 14.9508 6.96447L11.4153 10.5L14.9508 14.0355C15.1383 14.2231 15.2437 14.4774 15.2437 14.7426C15.2437 15.0079 15.1383 15.2622 14.9508 15.4497C14.7633 15.6373 14.5089 15.7426 14.2437 15.7426C13.9785 15.7426 13.7241 15.6373 13.5366 15.4497L10.0011 11.9142L6.46552 15.4497C6.27799 15.6373 6.02363 15.7426 5.75842 15.7426C5.4932 15.7426 5.23885 15.6373 5.05131 15.4497C4.86377 15.2622 4.75842 15.0079 4.75842 14.7426C4.75842 14.4774 4.86377 14.2231 5.05131 14.0355L8.58684 10.5L5.05131 6.96447C4.86377 6.77693 4.75842 6.52258 4.75842 6.25736C4.75842 5.99214 4.86377 5.73779 5.05131 5.55025Z"
            fill="#262626"
          />
        </svg>
      </div>
      <div v-for="text in description.texts" :key="text">
        <transition name="fade" mode="out-in">
          <p
            class="description-text"
            :class="{ fade: description.closed }"
            v-show="description.closed"
          >
            {{ text }}
          </p>
        </transition>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.description {
  border-bottom: 1px solid var(--tertiaryContent);
  max-width: 75rem;

  background-color: var(--primarySurface);
  .description-header {
    display: flex;
    justify-content: space-between;
    margin: 1rem 0;

    .close {
      cursor: pointer;
    }
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: max-height 0.6s ease, opacity 0.3s ease;
    height: auto;
    max-height: 600px;
    opacity: 1;
  }

  .fade-enter-from,
  .fade-leave-to {
    max-height: 0;
    opacity: 0;
  }
  .description-text {
    color: var(--secondaryContent);
    margin-bottom: 1rem;
  }
}
</style>