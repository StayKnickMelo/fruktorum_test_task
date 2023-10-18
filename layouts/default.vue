<template lang='pug'>
#default
    .logo
        LogoMain
    slot
    FooterComp
    

  
</template>

<script setup>
import LogoMain from "../components/UI/LogoMain.vue"
import FooterComp from '../components/UI/FooterComp.vue'
</script>

<style lang="scss" scoped> 
@import '~/assets/style/main.css';

#default{
    padding:28px 0;
    .logo{
        display: flex;
        justify-content: center;
        align-items: center;
    }

}

</style>