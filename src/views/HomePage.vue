
<script setup>
import { onMounted, reactive } from "vue";
import CardExpertise from "../components/MonExpertise/CardExpertise.vue";
const monExpertises = reactive([
  {
    title: "Identité de marque",
    subTitle: "2 packs",
    active: false,
  },
  {
    title: "Conception UI",
    subTitle: "2 packs",
    active: false,
  },
  {
    title: "Démarche UX",
    active: false,
  },
]);

const onChangeCard = (id) => {
  monExpertises.forEach((expertise, index) => {
    expertise.active = index === id;
  });
};
onMounted(() => {
  onChangeCard(0);
});
</script>
<template>
  <div>
    <section class="mon-expertise">
      <h3>Mon expertise</h3>
      <div class="cardExpertises">
        <div
          v-for="(monExpertise, index) in monExpertises"
          :key="monExpertise.title"
        >
          <CardExpertise
            :title="monExpertise.title"
            :subTitle="monExpertise.subTitle ? monExpertise.subTitle : ''"
            :active="monExpertise.active"
            @click="onChangeCard(index)"
          />
        </div>
      </div>
    </section>
  </div>
</template>


<style lang="scss" scoped>
.mon-expertise {
  h3 {
    color: #404040;
    margin-left: 3rem;
  }

  .cardExpertises {
    display: flex;
    flex-direction: row;
    margin-left: 3rem;
    gap: 1rem;
  }
}
</style>