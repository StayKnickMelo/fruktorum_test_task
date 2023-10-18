<template lang='pug'>
#articlepage
	.container(v-if="data?.body.length")
		.articlepage-block(v-for="(block, index) in data.body", :key="index")
			component(:is="localComponents[block.type]", :data="block.data")
</template>

<script setup>
import article_intro_block from "../components/ArticleIntro.vue";
import text_block from "../components/ArticleTextBlock.vue";
import image_block from "../components/ArticleImageBlock.vue";
import slider_block from "../components/ArticleSwiper.vue";
import subscribe_form_block from "../components/UI/Subscribe.vue";
import article_list_block from "../components/ArticleListBlock.vue";
import cta_form_block from "../components/ContactForm.vue";

//- article-3 ids of swiper block  are the same

const route = useRoute();

const { data } = await useAsyncData("page", () =>
	$fetch("https://devtwit8.ru/api/v1/page/", {
		params: {
			path: route.path,
		},
	})
);

useHead({
	title: data.value.meta.title,
	meta: [
		{
			name: "description",
			content: data.value.meta.description,
		},
	],
});

const localComponents = {
	article_intro_block,
	text_block,
	image_block,
	slider_block,
	subscribe_form_block,
	article_list_block,
	cta_form_block,
};
</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";
#articlepage {
	margin: 30px 0;
	@media (min-width: 1200px) {
		margin-bottom: 200px;
	}

	.container {
		display: flex;
		flex-direction: column;
		gap: 100px;
	}
}
</style>