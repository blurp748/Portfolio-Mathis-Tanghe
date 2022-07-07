<template>
  <div class="page">
    <n-card class="card reveal fade-left" :bordered="false">
      <h1>Bonjour,</h1>
      <br />
      Actuellement en troisième année de licence en informatique, je m'épanouis
      complétement dans mon domaine.<br />
      J'aime le développement et j'aimerais en connaître toujours plus sur les
      technologies que je manipule.<br />
      J'adore partager mes connaissances et apprendre des autres.
    </n-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from "vue";
import { NCard } from "naive-ui";

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

export default defineComponent({
  components: {
    NCard,
  },
  setup() {

    onMounted(() => {
      setTimeout(() => {
        reveal();
      }, 500)
    });

  }
});
</script>

<style scoped>
.page {
  width: 100vw;
  height: 100vh;
}

@media screen and (min-width: 721px) {
  .page {
    background-image: url("../assets/profil.jpg");
    background-repeat: no-repeat;
    background-size: cover;
  }
  .card {
    max-width: 30%;
    display: flex;
    margin: auto;
    top: 30vh;
    left: 20%;
    border-radius: 30px;
  }
}
@media screen and (max-width: 720px) {
  .page {
    background-image: url("../assets/black.png");
    background-repeat: no-repeat;
    background-size: cover;
  }

  .card {
    max-width: 80%;
    display: flex;
    margin: auto;
    top: 20%;
    color: white;
    background: rgba(0, 0, 0, 0.1);
    border-radius: 30px;
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
  animation: myAnim 1s ease 0s 1 normal forwards;
}

@keyframes myAnim {
	0% {
		transform: scale(0.5);
		transform-origin: 50% 100%;
	}

	100% {
		transform: scale(1);
		transform-origin: 50% 100%;
	}
}
</style>
