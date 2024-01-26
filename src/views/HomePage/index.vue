
<script setup>
import { onMounted, reactive, ref } from "vue";
import CardExpertise from "./Components/MonExpertise/CardExpertise.vue";
import ContentCard from "./Components/MonExpertise/ContentCard.vue";
import CardPrice from "./Components/MonExpertise/CardPrice.vue";

const monExpertises = reactive([
  {
    title: "Identité de marque",
    subTitle: "2 packs",
    active: false,
    contents: [
      {
        title: "Processus de conception",
        active: true,
        text: [
          "Je prends en charge l'intégralité du processus de conception de votre marque, en intégrant son utilisation numérique. Mes services sont axés sur la création d’une identité visuelle et émotionnelle percutante, mémorable.",
        ],
      },
      {
        title: "Identité Graphique",
        active: false,
        text: [
          "Je conçois un logo unique, capturant l'essence de votre marque pour une première impression mémorable. Je conçois également des variations du logo adaptées à différents contextes d’utilisation, préservant l'intégrité visuelle.",
          "Je sélectionne des typographies et couleurs cohérentes, ajoutant une dimension à l’identité de votre marque.",
          "Lors de cette étape du processus, j’apporte une attention particulière au respect des ‘best practices’ concernant l’accessibilité pour un usage numérique",
        ],
      },
      {
        title: "Guide Complet d'Identité de Marque",
        active: false,
        text: [
          "Votre marque mérite d'être utilisée avec cohérence. Je fournis un guide détaillé, tant pour une utilisation physique que digitale, vous indiquant comment appliquer votre identité visuelle de manière uniforme, assurant ainsi une présence forte et unifiée.",
        ],
      },
      {
        title: "Support de design collatéral",
        active: false,
        text: [
          "Au-delà du logo, je peux concevoir des supports de design collatéral, tels que des visuels pour les réseaux sociaux, des cartes de visite et bien plus encore. Je m'adapte à vos besoins spécifiques.",
        ],
      },
    ],
    prices: [
      {
        title: "Identité de marque Simple",
        subTitle: "Idéal pour débuter",
        descriptions: [
          "1 Moodboard ",
          "Logo et Responsive",
          "Couleurs & Typographies",
          "Charte Graphique",
          "Recommandations d’accessibilité",
        ],
        amount: "750",
      },
      {
        title: "Identité de marque Complète",
        subTitle: "Pour se démarquer et être mémorable",
        descriptions: [
          "2 Moodboards",
          "Logo et variations",
          "Couleurs & Typographies",
          "Éléments Graphiques",
          "Guide d’identité de marque",
          "Recommandations d’accessibilité",
          "2 Designs Collatéraux (Kit Social, Carte de visite, Flyers...)",
        ],
        amount: "1200",
      },
    ],
  },
  {
    title: "Conception UI",
    subTitle: "2 packs",
    active: false,
    contents: [
      {
        title: "Conception Multiplateforme",
        active: true,
        text: [
          "Votre présence digitale s'étend bien au-delà d'un simple site web. Je suis là pour concevoir des interfaces exceptionnelles adaptées à une variété de supports, que ce soit une application mobile, un site web dynamique ou un tableau de bord.",
        ],
      },
      {
        title: "Design Responsive",
        active: false,
        text: [
          "La flexibilité est la clé. Chacune de mes créations est pensée pour être entièrement réactive, garantissant une expérience utilisateur cohérente et agréable, quel que soit le dispositif utilisé.",
        ],
      },
      {
        title: "Accessibilité Numérique",
        active: false,
        text: [
          "L'inclusion est au cœur de mon approche. Je m'assure que chaque interface que je crée est accessible à tous, respectant les normes d'accessibilité en vigueur mais également des bonnes pratiques pour garantir une expérience utilisateur sans barrières.",
        ],
      },
      {
        title: "Éco-Conception",
        active: false,
        text: [
          "La durabilité compte. Mes designs intègrent des pratiques éco-responsables pour minimiser l'empreinte environnementale, sans compromettre la qualité ni les performances.",
        ],
      },
      {
        title: "Maquette Statique ou Prototype Interactif",
        active: false,
      },
    ],
    prices: [
      {
        title: "Site Vitrine Simple",
        subTitle: "1 à 3 pages",
        descriptions: [
          "Maquettes Statiques",
          "Élaboration du guide de style",
          "Responsive",
        ],
        amount: "450",
      },
      {
        title: "Site Vitrine Avancé",
        subTitle: "Plus de 5 pages",
        descriptions: [
          "Élaboration du guide de style",
          "Responsive",
          "Prototype Interactif",
        ],
        amount: "750",
      },
    ],
  },
  {
    title: "Démarche UX",
    active: false,
    contents: [
      {
        title: "Audit de votre produit",
        active: true,
        text: [
          "Comprendre les points forts et les zones d'amélioration est essentiel. Je commence par un audit approfondi de votre produit, analysant chaque élément pour identifier les opportunités d'optimisation et les pistes d'amélioration.",
        ],
      },
      {
        title: "Analyse des données",
        active: false,
        text: [
          "Les données sont des précieux indicateurs. Je m'appuie sur des analyses approfondies pour comprendre le comportement des utilisateurs, les tendances du marché et les performances de votre produit, orientant ainsi mes choix de conception.",
        ],
      },
      {
        title: "Tests Utilisateurs",
        active: false,
        text: [
          "L'amélioration continue est une philosophie où la voix de l’utilisateur est au centre de tout. Je mets en place des tests utilisateur pour évaluer la performance de votre produit, assurant ainsi une évolution basée sur des données concrètes.",
          "Puis je les étudies et réalise un compte-rendu ",
        ],
      },
      {
        title: "Personae",
        active: false,
        text: [
          "Chaque utilisateur est unique. ",
          "Je crée des personas détaillées, représentant différentes facettes de votre audience cible, pour garantir une approche personnalisée dans la conception.",
        ],
      },
      {
        title: "Parcours Utilisateur Stratégique",
        active: false,
        text: [
          "Je trace des parcours utilisateur stratégiques, anticipant chaque interaction, pour garantir une navigation fluide et une satisfaction utilisateur maximale.",
        ],
      },
    ],
  },
]);

const indexExpertise = ref(0);

const onChangeCard = (id) => {
  monExpertises.forEach((expertise, index) => {
    expertise.active = index === id;
  });
  indexExpertise.value = id;
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
      <div class="contentExpertises">
        <ContentCard
          :class="{
            card1:
              monExpertises[indexExpertise] &&
              monExpertises[indexExpertise].prices,
          }"
          :contents="monExpertises[indexExpertise].contents"
        />
        <CardPrice
          class="card2"
          v-if="
            monExpertises[indexExpertise] &&
            monExpertises[indexExpertise].prices
          "
          :prices="monExpertises[indexExpertise].prices"
        />
      </div>
    </section>
  </div>
</template>


<style lang="scss" scoped>
.mon-expertise {
  h3 {
    color: #404040;
    margin: 2rem 3rem;
  }

  .cardExpertises {
    display: flex;
    flex-direction: row;
    margin-inline: 3rem;

    gap: 1rem;
  }

  .contentExpertises {
    display: flex;
    margin-inline: 3rem;
    margin-top: 2rem;
    padding: 1rem;
    gap: 2rem;
    .card1 {
      flex: 0 0 65%;
    }
    .card2 {
      flex: 0 0 30%;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }
  }
}
</style>