<template lang="pug">
.fooditem  
    .container(style="direction:rtl")
    span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3.mt-3 {{element[0]?.category.slug.split('-').join(" ")}}
    
    div(v-html="textdata" :key="textdata" v-if="element[0]")
    Advertisevue(ad="2")
</template>

<script lang="ts" setup>
const route = useRoute();
const { data } = useAsyncGql({
  operation: "getfood"
});
let textdata = ref("");
let element = ref("");
onBeforeMount(() => {
  const foodarr = data?.value?.Article;
  console.log("foodarr", foodarr);

  const item = foodarr?.filter(e => {
    return e.slug === route.params.slug;
  });
  element.value = item;
  console.log(item);
  const title = item[0]?.translations[0].title;
  const articles = item[0]?.category.articles;
  const htmldata = articles?.filter(e => e.translations[0]?.title === title);

  const htmltext = htmldata[0]?.translations[0].content;
  textdata.value = htmltext;
  console.log(textdata.value);
});
</script>

<style lang="scss">
</style>