<template>
  <div class="pageBig">
    <n-carousel ref="carouselRef" autoplay :interval=2000 draggable>
      <n-button
        @click="handleClick('https://github.com/blurp748/ProjetGraph')"
        class="carousel-button"
      >
        <img class="carousel-img" src="../assets/graph.png" />
      </n-button>
      <n-button
        @click="handleClick('https://github.com/blurp748/QuestMaster')"
        class="carousel-button"
      >
        <img class="carousel-img" src="../assets/questMaster.png" />
      </n-button>
    </n-carousel>
  </div>
  <div class="pageTiny">
    <h1 class="titleTiny">Mes Projets</h1>
    <n-card @click="handleClick('https://github.com/blurp748/ProjetGraph')" class="card" title="Projet Graphe">
      Projet pour apprendre qu'est ce qu'un graphe de connaissances. <br/>Basé sur des concepts comme l'Ontologie et la Terminologie .
    </n-card>
    <n-card @click="handleClick('https://github.com/blurp748/QuestMaster')" class="card" title="QuestMaster">
      Mon premier jeu sur Unity pour apprendre les bases.
    </n-card>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { NCarousel, NButton, NCard } from "naive-ui";

export default defineComponent({
  components: {
    NCarousel,
    NButton,
    NCard,
  },
  setup() {
    function handleClick(link: string) {
      window.open(link);
    }

    return {
      handleClick,
    };
  },
});
</script>

<style scoped>

@media screen and (min-width: 721px) {
  .pageBig {
    width: 100vw;
    height: 100vh;
  }
  .pageTiny {
    display: none;
  }
  .carousel-img {
    width: 100%;
    height: 100%;
  }
  .carousel-button {
    width: 100%;
    height: 100%;
    background: black;
  }

  .carousel-button:hover {
    background: black;
  }
  .carousel-button:focus {
    background: black;
  }
}
@media screen and (max-width: 720px) {

  .pageTiny {
    width: 100vw;
    height: 100vh;
    background: white;
  }

  .pageBig {
    display: none;
  }

  .card {
    max-width: 80%;
    display: flex;
    margin: auto;
    border-radius: 30px;
    border-color: black;
    margin-top: 10vh;
  }

  .titleTiny {
    margin: 10px;
  }
}
</style>
