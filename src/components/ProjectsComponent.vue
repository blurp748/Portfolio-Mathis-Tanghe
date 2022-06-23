<template>
	<div class ="page">
		<n-carousel autoplay touchable>
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
}

.carousel-img {
  width: 100%;
  height: 100%;
}
</style>