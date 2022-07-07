<template>
  <div class="page">
    <div class="image reveal fade-left">
      <n-image class="img" :src="image" />
    </div>
    <h1 class="title">Cliquez pour agrandir</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { NImage } from "naive-ui";
import image from "../assets/cv.png";

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
    NImage,
  },
  setup() {
    return {
      image,
    };
  },
});
</script>

<style scoped>
.page {
  overflow: unset;
  width: 100vw;
  height: 100vh;
  background-image: url("../assets/grey2.png");
  background-repeat: no-repeat;
  background-size: cover;
}
.title {
  display: flex;
  justify-content: center;
  padding: 10px;
  margin-block: 0;
}
.image {
  display: flex;
  padding-top: 10vh;
  height: 75%;
}

.img {
  justify-content: center;
  width: 100vw;
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
