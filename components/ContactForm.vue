<template lang='pug'>
.contactform
	img.contactform-top(src="~/assets/img/form_img.jpeg")
	.contactform-bottom
		h2.title Стань участником проекта
		form(@submit.prevent)
			input(
				v-for="inputItem in inputList",
				:key="inputItem.id",
				:type="inputItem.type",
				:id="inputItem.id",
				:placeholder="inputItem.placeholder",
				v-model="formData[inputItem.id]"
			)
			button.blue(type="submit") Присоединиться
</template>

<script setup>
import { ref } from "vue";
const formData = ref({
	name: "",
	phone: "",
	email: "",
});
const inputList = [
	{
		id: "name",
		placeholder: "Имя",
		type: "text",
	},
	{
		id: "phone",
		placeholder: "Телефон",
		type: "number",
	},
	{
		id: "email",
		placeholder: "Email",
		type: "email",
	},
];
</script>

<style lang='scss' scoped>
@import "~/assets/style/main.css";

.contactform {
	background: var(--bg-dark);
	padding: 24px;
	display: flex;
	flex-direction: column;
	gap: 24px;
	@media (min-width: 1200px) {
		padding: 60px;
		gap: 60px;
		flex-direction: row;
	}

	img {
		height: 326px;
		width: 100%;
		object-fit: cover;
	}

	&-bottom {
		.title {
			font-family: var(--font-monserrat);
			color: #fff;
			@media (min-width: 1200px) {
				font-size: 34px;
			}
		}

		form {
			margin-top: 50px;

			input {
				&:not(:first-child) {
					margin-top: 25px;
				}
			}
		}

		button {
			margin-top: 50px;
			@media (min-width: 1200px) {
				margin-top: 66px;
			}
		}
	}
}
</style>