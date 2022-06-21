<template>
	<div class ="page">
		<n-timeline class="timeline" horizontal>
			<n-timeline-item
			type="success"
			title="Success"
			content="success content"
			time="2018-04-03 20:46"
			/>
			<n-timeline-item
			type="success"
			title="Success"
			content="success content"
			time="2018-04-03 20:46"
			/>
			<n-timeline-item
			type="success"
			title="Success"
			content="success content"
			time="2018-04-03 20:46"
			/>
			<n-timeline-item
			type="success"
			title="Success"
			content="success content"
			time="2018-04-03 20:46"
			/>
			<n-timeline-item content="Oops" />
		</n-timeline>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import { NTimeline, NTimelineItem } from 'naive-ui'

export default defineComponent({
	components: {
		NTimeline,
		NTimelineItem,
	},
});
</script>

<style scoped>
.page {
	width: 100vw;
	height: 100vh;
}
.timeline {
	align-items: center;
}
</style>