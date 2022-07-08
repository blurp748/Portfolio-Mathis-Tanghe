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
    <div class="lines">
      <div class="line"></div>
      <div class="line"></div>
      <div class="line"></div>
    </div>
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
  .lines {
    display: none;
  }
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

  .card {
    max-width: 80%;
    display: flex;
    margin: auto;
    top: 20%;
    color: white;
    background: rgba(0, 0, 0, 0);
    z-index:10;
  }

  .lines {
    display: table;
    width: 100vw;
    height: 100vh;
    background-color: #171717;
    color: #000;
    line-height: 1.6;
    position: relative;
    font-family: sans-serif;
    overflow: hidden;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 100vh;
    margin: auto;
    width: 100vw;
  }
  
  .line {
    position: absolute;
    width: 1px;
    height: 100%;
    top: 0;
    left: 50%;
    background: rgba(255, 255, 255, 0.1);
    overflow: hidden;
  }

  .line::after {
    content: '';
    display: block;
    position: absolute;
    height: 15vh;
    width: 100%;
    top: -50%;
    left: 0;
    background: linear-gradient(to bottom, rgba(255, 255, 255, 0) 0%, #ffffff 75%, #ffffff 100%);
    animation: drop 7s 0s infinite;
    animation-fill-mode: forwards;
    animation-timing-function: cubic-bezier(0.4, 0.26, 0, 0.97);
  }
  
  .line:nth-child(1) {
    margin-left: -25%;
  }

  .line:nth-child(1)::after {
    animation-delay: 2s
  }

  .line:nth-child(3) {
    margin-left: 25%;
  }

  .line:nth-child(3)::after {
    animation-delay: 2.5s
  }
    
  @keyframes drop {
    0% {
      top: -50%;
    }
    100% {
      top: 110%;
    }
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
