<template lang="pug">
.category
    .container    
        .head.py-5
            img(:src="'https://board.humm.world/assets/' + availabelhead(categorydata[0] )")
        h1.text-center.py-3 {{category }}
        .row
            .item.col-lg-3.col-sm-6.mt-3(v-for="item in categorydata") 
                nuxt-link(:to="'/food/'+item.slug"): Card(color="light")
                    .img
                        img(:src="'https://board.humm.world/assets/'+ srcavailable(item) ")
                    .data    
                        nuxt-link(:to="'/food/category/'+item.category.slug"): span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3 {{category}}
                        p.fw-bolder.mt-2 {{item.translations[0].title}}
                        
                    .user
                        p 
                            img(src="@/assets/images/user.png", alt="").me-2
                            span {{fullname(item)}}
                        p 
                            img(src="@/assets/images/clock.png", alt="").me-2 
                            span {{date(item.date_created)}}

</template>

<script lang="ts" setup>
const route = useRoute();
const title = route.params.category;
const category = title.split("-").join(" ");
const { data } = await useAsyncGql({
  operation: "getfood"
});
const food = data.value.Article;
const categorydata = food.filter(e => e.category.slug === title);
console.log(categorydata);
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
function availabelhead(item) {
  if (category === "dessert" || category === "breakfast") {
    return item.category.translations[1]?.cover?.id;
  } else if (item.category.translations[0]?.cover?.id) {
    return item.category.translations[0]?.cover?.id;
  } else {
    return item.category.translations[1]?.cover?.id;
  }
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
.head {
  img {
    width: 100%;
  }
}
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