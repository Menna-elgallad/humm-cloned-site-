<template lang="pug">
.mycard(:class="[color]")
    slot
    
</template>

<script setup lang="ts">
const props = defineProps({
    color: String
})

</script>

<style lang="scss" scoped>
.mycard{
    transition: all 0.5s ease;
    height: 100%;
    &.light{
        border: 1px solid black;
        padding: 1.2rem;
        cursor: pointer;
        // width: fit-content;
        transition: all 0.3s ease-out;
        &:hover{
            box-shadow: 7px 4px 0 black;
        }
    }
    &.dark{
        border: 1px solid white !important;
        padding: 1.2rem;
        cursor: pointer;
        // width: fit-content;
        color: white !important;
        transition: all 0.3s ease-out;
        &:hover{
            box-shadow: 7px 4px 0 white !important;
        }
    }
    &.static{
        border: 1px solid black !important;
        padding: 1.2rem;
        cursor: pointer;
        box-shadow: 7px 4px 0 black !important;
        
    }
    

}

</style>