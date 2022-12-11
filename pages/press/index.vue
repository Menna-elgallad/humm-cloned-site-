<template lang="pug">
.section1.main-margin
    .container
        .head.d-flex.justify-content-between
            h2 Food

        press(:limit="internallimit" :key="internallimit" ) 
        .d-flex.justify-content-center.py-3
            Cardbutton(color="light" @click="limitinc()") Show More 
    .section2.main-margin
        .container
            Advertisevue(ad="1")   
    
</template>

<script setup lang="ts">
let internallimit = ref(3)


function limitinc(){
    internallimit.value +=4
}

</script>

<style>

</style>