<template lang='pug'>
#main
    .container(v-if="data?.body?.[0]?.data?.articles")
        NewsCard(v-for="newsCard in data?.body?.[0]?.data?.articles" :key="newsCard.image" :newsCard="newsCard")
        
  
</template>

<script setup>
import {ref} from 'vue'
import NewsCard from '../components/ArticleCard.vue'

const {data} = await useAsyncData('page', ()=> $fetch('https://devtwit8.ru/api/v1/page/',{
    params: {
        path: '/'
    }
}))

useHead({
	title: data.value.meta.title,
	meta: [
		{
			name: "description",
			content: data.value.meta.description,
		},
	],
});

</script>

<style lang="scss" scoped>
@import '~/assets/style/main.css';

#main{
    margin:30px 0;
    .container{
        display: flex;
        flex-direction: column;
        gap:30px;

        @media (min-width: 1200px){
            display: grid;
            grid-template-columns: repeat(3, 1fr);
        }

    }
}

</style>