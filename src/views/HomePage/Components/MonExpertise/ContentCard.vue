<script setup >
const props = defineProps({
  contents: Array,
});

const toggleActive = (clickedIndex) => {
  return props.contents.map((content, index) => {
    const isActive = index === clickedIndex && !content.active;
    return { ...content, active: isActive };
  });
};
</script>

<template>
  <div class="contents">
    <div
      v-for="(content, index) in contents"
      :key="content.title"
      class="description"
    >
      <div class="description__header" @click="contents = toggleActive(index)">
        <b class="label">
          {{ content.title }}
        </b>
        <span v-if="content.text"
          ><img src="../../../../assets/Close.svg" alt=""
        /></span>
      </div>
      <transition name="fadeHeight">
        <div v-if="content.active">
          <div
            v-for="text in content.text"
            :key="text"
            class="description__text"
          >
            {{ text }}
          </div>
        </div>
      </transition>
      <hr />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.contents {
  background-color: var(--primarySurface);
  .description {
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;

    &__header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1rem;
      cursor: pointer;
    }
    hr {
      margin: 1rem 0;
    }

    &__text {
      color: var(--tertiaryContent);
    }
  }
  .fadeHeight-enter-active,
  .fadeHeight-leave-active {
    transition: all 0.2s;
    max-height: 400px;
  }
  .fadeHeight-enter,
  .fadeHeight-leave-to {
    opacity: 0;
    max-height: 0px;
  }
}
</style>