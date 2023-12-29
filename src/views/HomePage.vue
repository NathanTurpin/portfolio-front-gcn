
<script setup>
import { onMounted, reactive, ref } from "vue";
import CardExpertise from "../components/MonExpertise/CardExpertise.vue";
import CardDescription from "../components/MonExpertise/CardDescription.vue";
import CardPacks from "../components/MonExpertise/CardPacks.vue";

const monExpertises = reactive([
  {
    title: "Identité de marque",
    subTitle: "2 packs",
    active: false,
    packs: [
      {
        title: "Identité de marque Simple",
        subTitle: "Idéal pour débuter",
        lists: [
          "1 Moodboard ",
          "Logo et Responsive",
          "Couleurs & Typographies",
          "Charte Graphique",
          "Recommandations d’accessibilité",
        ],
        price: "750€",
      },
      {
        title: "Identité de marque Complète",
        subTitle: "Pour se démarquer et être mémorable",
        lists: [
          "2 Moodboards",
          "Logo et variations",
          "Couleurs & Typographies",
          "Éléments Graphiques",
          "Guide d’identité de marque",
          "Recommandations d’accessibilité",
          "2 Designs Collatéraux (Kit Social, Carte de visite, Flyers...)",
        ],
        price: "1200€",
      },
    ],
    descriptions: [
      {
        title: "Processus de conception",
        texts: [
          "Je prends en charge l'intégralité du processus de conception de votre marque, en intégrant son utilisation numérique. Mes services sont axés sur la création d’une identité visuelle et émotionnelle percutante, mémorable.",
        ],
        closed: true,
      },
      {
        title: "Identité Graphique",
        texts: [
          "Je conçois un logo unique, capturant l'essence de votre marque pour une première impression mémorable. Je conçois également des variations du logo adaptées à différents contextes d’utilisation, préservant l'intégrité visuelle. Je sélectionne des typographies et couleurs cohérentes, ajoutant une dimension à l’identité de votre marque.",
          "Lors de cette étape du processus, j’apporte une attention particulière au respect des ‘best practices’ concernant l’accessibilité pour un usage numérique",
        ],
        closed: true,
      },
      {
        title: "Guide Complet d'Identité de Marque",
        texts: [
          "Votre marque mérite d'être utilisée avec cohérence. Je fournis un guide détaillé, tant pour une utilisation physique que digitale, vous indiquant comment appliquer votre identité visuelle de manière uniforme, assurant ainsi une présence forte et unifiée.",
        ],
        closed: true,
      },
      {
        title: "Support de design collatéral",
        texts: [
          "Au-delà du logo, je peux concevoir des supports de design collatéral, tels que des visuels pour les réseaux sociaux, des cartes de visite et bien plus encore. Je m'adapte à vos besoins spécifiques.",
        ],
        closed: true,
      },
    ],
  },
  {
    title: "Conception UI",
    subTitle: "2 packs",
    active: false,
    packs: [
      {
        title: "Site Vitrine Simple",
        subTitle: "1 à 3 pages",
        lists: [
          "Maquettes Statiques",
          "Élaboration du guide de style",
          "Responsive",
        ],
        price: "450€",
      },
      {
        title: "Site Vitrine Avancé",
        subTitle: "Plus de 5 pages",
        lists: [
          "Prototype Interactif",
          "Elaboration du guide de style",
          "Responsive",
        ],
        price: "750€",
      },
    ],
    descriptions: [
      {
        title: "Conception Multiplateforme",
        texts: [
          "Votre présence digitale s'étend bien au-delà d'un simple site web. Je suis là pour concevoir des interfaces exceptionnelles adaptées à une variété de supports, que ce soit une application mobile, un site web dynamique ou un tableau de bord.",
        ],
        closed: true,
      },
      {
        title: "Design Responsive",
        texts: [
          "La flexibilité est la clé. Chacune de mes créations est pensée pour être entièrement réactive, garantissant une expérience utilisateur cohérente et agréable, quel que soit le dispositif utilisé.",
        ],
        closed: true,
      },
      {
        title: "Accessibilité Numérique",
        texts: [
          "L'inclusion est au cœur de mon approche. Je m'assure que chaque interface que je crée est accessible à tous, respectant les normes d'accessibilité en vigueur mais également des bonnes pratiques pour garantir une expérience utilisateur sans barrières.",
        ],
        closed: true,
      },
      {
        title: "Éco-Conception",
        texts: [
          "La durabilité compte. Mes designs intègrent des pratiques éco-responsables pour minimiser l'empreinte environnementale, sans compromettre la qualité ni les performances.",
        ],
        closed: true,
      },
      {
        title: "Maquette Statique ou Prototype Interactif",
        texts: [""],
        closed: true,
      },
    ],
  },
  {
    title: "Démarche UX",
    active: false,
    descriptions: [
      {
        title: "Audit de votre produit",
        texts: [
          "Comprendre les points forts et les zones d'amélioration est essentiel. Je commence par un audit approfondi de votre produit, analysant chaque élément pour identifier les opportunités d'optimisation et les pistes d'amélioration.",
        ],
        closed: true,
      },
      {
        title: "Analyse des données",
        texts: [
          "Les données sont des précieux indicateurs. Je m'appuie sur des analyses approfondies pour comprendre le comportement des utilisateurs, les tendances du marché et les performances de votre produit, orientant ainsi mes choix de conception.",
        ],
        closed: true,
      },
      {
        title: "Tests Utilisateurs",
        texts: [
          "L'amélioration continue est une philosophie où la voix de l’utilisateur est au centre de tout. Je mets en place des tests utilisateur pour évaluer la performance de votre produit, assurant ainsi une évolution basée sur des données concrètes.",
          "Puis je les étudies et réalise un compte-rendu ",
        ],
        closed: true,
      },
      {
        title: "Personae",
        texts: [
          "Chaque utilisateur est unique. ",
          "Je crée des personas détaillées, représentant différentes facettes de votre audience cible, pour garantir une approche personnalisée dans la conception.",
        ],
        closed: true,
      },
      {
        title: "Parcours Utilisateur Stratégique",
        texts: [
          "Je trace des parcours utilisateur stratégiques, anticipant chaque interaction, pour garantir une navigation fluide et une satisfaction utilisateur maximale.",
        ],
        closed: true,
      },
    ],
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
            :subTitle="monExpertise.subTitle ?? ''"
            :active="monExpertise.active"
            :packs="monExpertise.packs ?? ''"
            :descriptions="monExpertise.descriptions"
            @click="onChangeCard(index)"
          />
        </div>
      </div>
      <div class="cardDescriptions">
        <div v-for="monExpertise in monExpertises" :key="monExpertise.title">
          <transition name="slide-fade">
            <div v-if="monExpertise.active" class="cardInfos">
              <CardDescription :descriptions="monExpertise.descriptions" />
              <CardPacks :packs="monExpertise.packs" />
            </div>
          </transition>
        </div>
      </div>
    </section>
  </div>
</template>


<style lang="scss" scoped>
.slide-fade-leave-active,
.slide-fade-enter-active {
  transition: all 0.3s ease;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
}
.mon-expertise {
  height: 500px;
  h3 {
    color: #404040;
  }
  width: 90%;
  margin: auto;
  height: 100dvh;
  .cardExpertises {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    margin-top: 1.5rem;
  }
  .cardDescriptions {
    margin-top: 2rem;
    .cardInfos {
      display: grid;
      grid-template-columns: 2.5fr 1fr;
      gap: 1.5rem;
    }
  }
}
</style>