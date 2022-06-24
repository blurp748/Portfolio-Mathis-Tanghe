<template>
  <div class="page">
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
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { NCarousel, NButton } from "naive-ui";

export default defineComponent({
  components: {
    NCarousel,
    NButton,
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
.page {
  width: 100vw;
  height: 100vh;
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
</style>
