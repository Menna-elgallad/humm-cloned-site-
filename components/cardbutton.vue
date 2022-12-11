<template lang="pug">
.mycard(:class="[color]") 
    a 
        slot
  
</template>

<script lang="ts" setup>
const props = defineProps({
  color: String
});
</script>

<style lang="scss" scoped>
.mycard {
  transition: all 0.5s ease;
  &.light {
    border: 1px solid black;
    box-shadow: 4px 3px 0 black;
    padding: 8px 1.5rem;
    /* text-align: center; */
    font-weight: 800;
    font-size: 15px;
    cursor: pointer;
    width: -moz-fit-content;

    &:hover {
      background-color: black;
      color: white;
      border: 1px solid white;
    }
  }
  &.dark {
    border: 1px solid white;
    box-shadow: 4px 3px 0 white;
    padding: 8px 1.5rem;
    /* text-align: center; */
    font-weight: 800;
    font-size: 15px;
    cursor: pointer;
    width: -moz-fit-content;
    width: fit-content;
    height: 40px;
    background-color: black;
    color: white !important;

    &:hover {
      background-color: white;
      color: black !important;
      border: 1px solid black;
    }
  }
}
</style>