<template lang='pug'>
.articlelist(v-if="data.articles.length")
	h2.articlelist-title(v-if="data.title") {{ data.title }}
	.articlelist-list
		ArticleCard(
			v-for="newsCard in data.articles",
			:key="newsCard.image",
			:newsCard="newsCard"
		)
</template>

<script setup>
import ArticleCard from "./ArticleCard.vue";

const props = defineProps({
	data: {
		type: Object,
		required: true,
	},
});
</script>

<style lang=scss scoped>
@import "~/assets/style/main.css";
.articlelist {
	&-title {
		font-family: var(--font-monserrat);
		color: var(--bg-dark);
	}

	&-list {
		margin-top: 50px;
		display: flex;
		flex-direction: column;
		gap: 30px;

		@media (min-width: 1200px) {
			display: grid;
			grid-template-columns: repeat(3, 1fr);
		}
	}
}
</style>