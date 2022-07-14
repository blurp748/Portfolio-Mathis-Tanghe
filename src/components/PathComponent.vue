<template>
  <div class="page">
    <div class="big reveal fade-left">
      <h1 class="title">Mon Parcours</h1>
      <n-timeline class="timeline" horizontal>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="grey"
        >
          <h4 class="title-item">Master Informatique (en cours)</h4>
          <div class="text-item">Université Savoie Mont Blanc</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="grey"
        >
          <h4 class="title-item">Développeur Web pour une PWA</h4>
          <div class="text-item">Laboratoire du LIRIS - Lyon</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="grey"
        >
          <h4 class="title-item">Licence Informatique</h4>
          <div class="text-item">Université Savoie Mont Blanc - Mention Bien</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="grey"
        >
          <h4 class="title-item">Développeur Android</h4>
          <div class="text-item">Projet tutoré pour l'Office nationale des forêts</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2017"
          color="grey"
        >
          <h4 class="title-item">Baccalauréat Scientifique</h4>
          <div class="text-item">Lycée des Glières - Annemasse</div>
        </n-timeline-item>
      </n-timeline>
    </div>
    <div class="tiny reveal fade-left">
      <h1 class="titleTiny">Mon Parcours</h1>
      <n-timeline class="timelineTiny">
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="whitesmoke"
        >
          <h4 class="title-item">Master Informatique (en cours)</h4>
          <div class="text-item">Université Savoie Mont Blanc</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="whitesmoke"
        >
          <h4 class="title-item">Développeur Web pour une PWA</h4>
          <div class="text-item">Laboratoire du LIRIS - Lyon</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="whitesmoke"
        >
          <h4 class="title-item">Licence Informatique</h4>
          <div class="text-item">Université Savoie Mont Blanc - Mention Bien</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2022"
          color="whitesmoke"
        >
          <h4 class="title-item">Développeur Android</h4>
          <div class="text-item">Projet tutoré pour l'Office nationale des forêts</div>
        </n-timeline-item>
        <n-timeline-item
          class="timeline-item"
          type="success"
          time="2017"
          color="whitesmoke"
        >
          <h4 class="title-item">Baccalauréat Scientifique</h4>
          <div class="text-item">Lycée des Glières - Annemasse</div>
        </n-timeline-item>
      </n-timeline>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { NTimeline, NTimelineItem } from "naive-ui";

function reveal() {

	const reveals = document.querySelectorAll(".reveal");

	for (let i = 0; i < reveals.length; i++) {
    const windowHeight = window.innerHeight;
    const elementTop = reveals[i].getBoundingClientRect().top;
    const elementVisible = 200;

    if (elementTop < windowHeight - elementVisible) {
      reveals[i].classList.add("active");
    } else {
      reveals[i].classList.remove("active");
    }
	}

}

window.addEventListener("scroll", reveal);

export default defineComponent({
  components: {
    NTimeline,
    NTimelineItem,
  },
});
</script>

<style scoped>
.page {
  height: 100vh;
  background-repeat: no-repeat;
  background-size: cover;
}
::-webkit-scrollbar {
  left: 65px;
}

@media screen and (min-width: 721px) {
  .timeline {
    top: 30vh;
    left: 15vw;
    overflow-x: overlay;
  }

  .title-item {
    color: whitesmoke;
  }

  .page {
    width: calc(100vw - 65px);
  }

  .text-item {
    color: grey;
  }

  .title {
    margin-block: 0;
    color: whitesmoke;
    padding: 50px;
  }

  .tiny {
    display: none;
  }
}
@media screen and (max-width: 720px) {
  .page {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    background-image: url("../assets/background_17.png");
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position: center;
  }
  .titleTiny {
    color: whitesmoke;
    text-align: center;
    margin-block: 0;
    margin-top: 10%;
    margin-bottom: 15%;
    background: #171717;
  } 

  .timelineTiny {
    display: flex;
    width: 80%;
    margin: auto;
    padding: 0;
    border-radius: 30px;
    background: #171717;
    line-height: 0.8;
  }

  .title-item {
    color: whitesmoke;
  }

  .text-item {
    color: grey;
  }

  .big {
    display: none;
  }
}

@media screen and (max-height: 620px) {
  .page {
    height: 120vh;
  }
}

.reveal {
  position: relative;
  opacity: 0;
}

.reveal.active {
  opacity: 1;
}

.active.fade-left {
  animation: fade-left 1s ease-in;
}

@keyframes fade-left {
  0% {
    transform: translateX(-100px);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}
</style>
