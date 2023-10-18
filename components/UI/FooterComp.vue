<template lang='pug'>
.footer
	.container
		.footer-top
			.footer-top-info
				LogoMain
				p {{ footerText }}
			.footer-top-contacts
				.email
					span email
					a(:href="email.href") {{ email.address }}
				.social
					a.social-item(
						v-for="socialItem in socialList",
						:key="socialItem.id",
						:href="socialItem.href"
						@click.prevent
					)
						component(:is="localComponents[socialItem.id]")
		Subscribe
</template>

<script setup>
import LogoMain from "./LogoMain.vue";
import Subscribe from "./Subscribe.vue";
import facebook from "../Icons/IconFacebook.vue";
import vk from "../Icons/IconVk.vue";
import insta from "../Icons/IconInsta.vue";
import telegram from "../Icons/IconTelegram.vue";

const localComponents = {
	facebook,
	vk,
	insta,
	telegram,
};

const footerText =
	"Cтатьи о дизайне и искусстве, которые исследуют творческие вдохновения и актуальные тенденции, раскрывая мир эстетики и креативности";
const email = {
	address: "testblogsupport@gmail.com",
	href: "mailto:testblogsupport@gmail.com",
};
const socialList = [
	{
		id: "facebook",
		href: "!#",
	},
	{
		id: "vk",
		href: "!#",
	},
	{
		id: "insta",
		href: "!#",
	},
	{
		id: "telegram",
		href: "!#",
	},
];
</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";

.footer {
	border-top: 1px solid #8d959c;
	padding-top: 50px;

	&-top {
		@media (min-width: 1200px) {
			display: flex;
			justify-content: space-between;
			align-items: center;
		}

		&-info {
			@media (min-width: 1200px) {
				max-width: 426px;
			}
			p {
				font-family: var(--font-monserrat);
				color: #8d959c;
				margin-top: 20px;
				font-size: 14px;
			}
		}

		&-contacts {
			margin-top: 24px;
			.email {
				font-family: var(--font-monserrat);
				display: flex;
				flex-direction: column;
				span {
					color: #8d959c;
					font-size: 14px;
				}

				a {
					color: #1b1b1b;
					font-size: 18px;
				}
			}

			.social {
				margin-top: 24px;
				display: flex;
				gap: 20px;
			}
		}
	}

	::v-deep(.subscribe) {
		margin-top: 24px;
		@media (min-width: 1200px) {
			margin-top: 70px;
		}
	}
}
</style>