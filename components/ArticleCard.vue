<template lang='pug'>
.newsCard
    img(:src="newsCard.image" :alt='newsCard.title')
    h3.newsCard-title(v-if="newsCard.title") {{newsCard.title}}
    nuxt-link(v-if="newsCard.link" :to="newsCard.link") Читать
    
</template>

<script setup>


const props = defineProps({
    newsCard:{
        type: Object,
        required: true
    }
})

</script>

<style lang="scss" scoped>
@import '~/assets/style/main.css';

.newsCard{
    img{
        height: 320px;
        object-fit: cover;
        width: 100%;
    }

    h3{
        font-family: var(--font-monserrat);
        font-weight: bold;
        margin-top:20px;
    }

    a{
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: var(--font-monserrat);
        height: 46px;
        width:164px;
        margin-top:30px;
        color: #fff;
        background: var(--bg-dark);
        transition:all ease-in-out .3s;

        &:hover{
            background: var(--bg-blue);
        }


    }
}

</style>