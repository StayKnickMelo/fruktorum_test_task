<template lang='pug'>
.articleimageblock
    img(:src="data.src" :alt="data.caption || 'image'")
    span(v-if="data.caption") {{data.caption}}

  
</template>

<script setup>
const props = defineProps({
    data:{
        type:Object,
        required: true
    }
})

</script>

<style lang="scss" scoped>
@import "~/assets/style/main.css";

.articleimageblock{
    img{
        height: 400px;
        border-radius: 2px 220px 2px  2px;
        object-fit: cover;
        width: 100%;

        @media (min-width: 1200px){
            height: 550px;
        }
    }

    span{
        color: #8D959C;
        font-family: var(--font-monserrat);
        display: block;
        margin-top:15px;
        text-align: end;
    }
}

</style>