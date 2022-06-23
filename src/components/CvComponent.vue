<template>
	<div class ="page">
		<div class="image">
			<n-image
				:src="image"
			/>
		</div>
		<h1 class="title">Cliquez pour agrandir</h1>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { NImage } from 'naive-ui'
import image from "../assets/cv.png"

export default defineComponent({
	components: {
		NImage,
	},
	setup() {
		return {
			image
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
	justify-content: center;
	padding-top: 10vh;
	height: 75%;
	max-height: 100vw;
}
</style>