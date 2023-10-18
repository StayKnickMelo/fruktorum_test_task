<template>
	<swiper
		class="swiper"
		:delete-instance-on-destroy="true"
		:slides-per-view="1"
		:navigation="{
			prevEl: prev,
			nextEl: next,
		}"
		:modules="modules"
	>
		<swiper-slide v-for="slide in data" :key="slide">
			<img :src="slide" alt="image" />
		</swiper-slide>
		<div ref="prev" class="swiper-button-prev">
			<IconArrowLeft />
		</div>
		<div ref="next" class="swiper-button-next">
			<IconArrowLeft />
		</div>
	</swiper>
</template>
  <script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from "swiper/modules";
import IconArrowLeft from "./Icons/IconArrowLeft.vue";
import { ref } from 'vue';

export default {
	components: {
		Swiper,
		SwiperSlide,
		IconArrowLeft,
	},
	props: {
		data: {
			type: Array,
			required: true,
		},
	},
	setup() {
		const prev = ref(null);
		const next = ref(null);
	
		return {
			modules: [Navigation],
			prev,
			next,
		};
	},
};
</script>

  <style lang='scss' scoped>
@import "swiper/css";

.swiper {
	position: relative;
	img {
		object-fit: cover;
		height: 400px;
		width: 100%;

		@media (min-width: 550px) {
			height: 550px;
		}
	}

	.swiper-button-prev,
	.swiper-button-next {
		display: flex;
		justify-content: center;
		align-items: center;
		background: var(--bg-dark);
		width: 60px;
		height: 60px;
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		z-index: 1;
		cursor: pointer;
	}

	&::v-deep(.swiper-slide) {
		@media (min-width: 1200px) {
			padding: 0 114px;
		}
	}

	.swiper-button-next {
		right: 0;
		&::v-deep(svg) {
			transform: rotate(180deg);
		}
	}
	.swiper-button-prev {
		left: 0;
	}
}
</style>