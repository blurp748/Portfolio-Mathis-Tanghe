<template>
	<div class ="page">
		<n-carousel autoplay dot-type="line">
			<img
			class="carousel-img"
			src="../assets/graph.png"
			>
			<img
			class="carousel-img"
			src="../assets/questMaster.png"
			>
		</n-carousel>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { NCarousel } from 'naive-ui'

export default defineComponent({
	components: {
		NCarousel,
	},
});
</script>

<style scoped>
.page {
	width: 100vw;
	height: 100vh;
	background-image: url("../assets/grey.jpg");
	background-repeat: no-repeat;
  	background-size: 100%;
}

.carousel-img {
  width: 100vw;
  height: 100vh;
  object-fit: cover;
}
</style>