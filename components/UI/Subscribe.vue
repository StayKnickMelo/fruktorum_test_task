<template lang='pug'>
form.subscribe(@submit.prevent)
	h3.subscribe-title Подпишись на рассылку
	.subscribe-group
		input(type="email", required, placeholder="Email")
		button.blue(type="submit") Подписаться
</template>

<script setup>
</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";

.subscribe {
	background: var(--bg-dark);
	padding: 35px 30px;

	@media (min-width: 1024px) {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	&-title {
		font-family: var(--font-monserrat);
		color: #fefefe;
	}

	&-group {
		display: flex;
		flex-direction: column;
		gap: 37px;
		margin-top: 24px;

		@media (min-width: 1024px) {
			margin-top: 0;
		}

		@media (min-width: 1020px) {
			flex-direction: row;
		}
	}
}
</style>