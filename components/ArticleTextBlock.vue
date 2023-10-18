<template lang='pug'>
.articletextblock
	.articletextblock-text(v-html="data")
</template>

<script setup>
const props = defineProps({
	data: {
		type: String,
		required: true,
	},
});
</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";

.articletextblock {
	&-text {
		font-family: var(--font-monserrat);
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
}
</style>