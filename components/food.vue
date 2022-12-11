<template lang="pug">
.food
    .load.d-flex.justify-content-center(v-if="isloading")
        span.loader
    .row(v-else)
        .item.col-lg-3.col-sm-6.mt-3(v-for="item in food") 
            nuxt-link(:to="'/food/'+item.slug"): Card(color="light")
                .img
                    img(:src="'https://board.humm.world/assets/'+ srcavailable(item) ")
                .data    
                    nuxt-link(:to="'/food/category/'+item.category.slug"): span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3 {{item.category.slug.split('-').join(" ")}}
                    p.fw-bolder.mt-2 {{item.translations[0].title}}
                    
                .user
                    p 
                        img(src="@/assets/images/user.png", alt="").me-2
                        span {{fullname(item)}}
                    p 
                        img(src="@/assets/images/clock.png", alt="").me-2 
                        span {{date(item.date_created)}}


</template>

<script setup lang="ts">
let isloading = ref(false);
let food = ref("");
const props = defineProps({
  limit: Number
});
async function foodfun() {
  isloading.value = true;
  const { data } = await useAsyncGql({
    operation: "getfood",
    variables: { limit: props.limit }
  });
  isloading.value = false;
  food.value = data.value?.Article;
}
foodfun();
console.log("food", food);
function date(str) {
  let char = "";
  for (let i = 0; i < str.length; i++) {
    if (str[i] === "T") {
      break;
    }
    char += str[i];
  }
  return char;
}
function srcavailable(item) {

  return item.translations[0]?.cover.id;
}
function fullname(item) {
  return (
    item?.category?.user_created?.first_name +
    " " +
    item?.category?.user_created.last_name
  );
}
</script>

<style lang="scss" scoped>
.item {
  p {
    margin: 0;
  }
  .img {
    img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }
  }
  .rounded-pill {
    &:hover {
      background-color: black;
      color: white;
    }
  }
  .user {
    p {
      img {
        width: 20px;
      }
      color: #777;
    }
  }
}
</style>