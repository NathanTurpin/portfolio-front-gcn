
<script setup>
import { onMounted, reactive, ref } from "vue";
import CardExpertise from "../components/MonExpertise/CardExpertise.vue";
import DiagramsExpertise from "../components/MonExpertise/DiagramsExpertise.vue";
const monExpertises = reactive([
  {
    title: "Identité de marque",
    subTitle: "2 packs",
    active: false,
    references: ref(["cardRef1", "rondRef1"]),
  },
  {
    title: "Conception UI",
    subTitle: "2 packs",
    active: false,
    references: ref(["cardRef2", "rondRef2"]),
  },
  {
    title: "Démarche UX",
    active: false,
    references: ref(["cardRef3"]),
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
            :references="monExpertise.references"
            @click="onChangeCard(index)"
          />
        </div>
      </div>
      <DiagramsExpertise />
    </section>
  </div>
</template>


<style lang="scss" scoped>
.mon-expertise {
  height: 500px;
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