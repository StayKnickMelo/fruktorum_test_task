<template lang='pug'>
.articleintro
	img(:src="data.image", :alt="data.title")
	.articleintro-info
		h1.articleintro-info-title(v-if="data.title") {{ data.title }}
		.articleintro-info-stats(v-if="data.reading_time || data.views_count")
			.group(v-if="data.reading_time")
				IconClock
				span {{ `${data.reading_time} мин время чтения` }}
			.group(v-if="data.views_count")
				IconEye
				span {{ `${data.views_count} 360 прочитали статью` }}
		p.articleintro-info-desc(v-if="data.short_description") {{ data.short_description }}
</template>

<script setup>
import IconClock from "./Icons/IconClock.vue";
import IconEye from "./Icons/IconEye.vue";

const props = defineProps({
	data: {
		type: Object,
		required: true,
	},
});
</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";

.articleintro {
	display: flex;
	flex-direction: column;
	gap: 31px;

	@media (min-width: 1200px) {
		flex-direction: row;
		align-items: center;
	}

	img {
		height: 580px;
		object-fit: cover;
		border-radius: 2px 220px 2px 2px;
		flex: 1;
	}

	&-info {
		flex: 1;
		&-title {
			font-family: var(--font-monserrat);
			color: var(--bg-dark);
			font-weight: bold;
			@media (min-width: 1200px) {
				font-size: 56px;
			}
		}

		&-stats {
			margin-top: 30px;
			display: flex;
			flex-direction: column;
			gap: 4px;

			.group {
				display: flex;
				align-items: center;
				gap: 8px;

				span {
					color: #8d959c;
					font-family: var(--font-monserrat);
					font-size: 14px;
				}
			}
		}

		&-desc {
			font-family: var(--font-monserrat);
			color: var(--bg-dark);
			font-size: 18px;
			margin-top: 50px;
		}
	}
}
</style>