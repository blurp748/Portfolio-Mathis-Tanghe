<template>
  <div class="page">
    <div class="image reveal fade-left">
      <n-image id="n_image" class="img" :src="image" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { NImage, NButton } from "naive-ui";
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
    NButton,
  },
  setup() {
    return {
      image,
      show() {
        const img = document.getElementById('n_image');
        if (img != null){
          img.style.visibility = "visible";
        }
      }
    };
  },
});
</script>

<style scoped>
.page {
  overflow: unset;
  width: 100vw;
  height: 100vh;
}
.image {
  display: flex;
}

.img {
  background: transparent;
  justify-content: center;
  width: 100vw;
}

@media screen and (max-width: 720px) {
  .image {
    padding-top: 25vh;
    height: 50%;
  }

  .page {
    background-image: url("../assets/background_19.png");
    background-repeat: no-repeat;
    background-size: cover;
  }
}

@media screen and (min-width: 721px) {
  .image {
    padding-top: 10vh;
    height: 75%;
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
