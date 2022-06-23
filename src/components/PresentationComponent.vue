<template>
	<div class ="page">
		<n-card class="card" :bordered="false">
			<h1>Bonjour, </h1><br/>
			Actuellement en troisième année de licence en
			informatique, je m'épanoui complétement dans mon
			domaine.<br />
			J'aime le développement et j'aimerai en
			connaître toujours plus sur les technologies que
			je manipule.<br />
			J'adore aider les gens, mais surtout leur
			apprendre des choses et qu'ils m'en apprennent
			aussi !
		</n-card>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { NCard } from 'naive-ui'

export default defineComponent({
	components: {
		NCard,
	},
});
</script>

<style scoped>
.page {
	width: 100vw;
	height: 100vh;
}

@media screen and (min-width: 721px) {
	.page {
		background-image: url("../assets/black.png");
		background-repeat: no-repeat;
		background-size: cover;
	}
	.card {
	max-width: 30%;
	display: flex;
	margin : auto;
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
	background: rgba(0,0,0,0.1);
	border-radius: 30px;
	}
}
</style>