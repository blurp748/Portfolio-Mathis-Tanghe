<template>
	<div class ="page">
		<n-card class="card" title="Bonjour,">
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
	background-image: url("../assets/grey.jpg");
	background-repeat: no-repeat;
  	background-size: 100%;
}
.card {
	max-width: 300px;
	display: flex;
	margin : auto;
	top: 35%;
	left: 20%;

}
</style>