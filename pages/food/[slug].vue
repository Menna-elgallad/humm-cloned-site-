<template lang="pug">
.fooditem.mt-4  
    .container(style="direction:rtl")
        .head.py-5
          iframe(width="100%" height="700px" :src="'https://www.youtube.com/embed/'+element[0]?.video" v-if="element[0]")

        .d-flex.content
            .recipe
                nuxt-link(:to="'/food/category/'+element[0]?.category.slug"): span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3.mt-3 {{element[0]?.category.slug.split('-').join(" ")}}
                h2.fw-bolder.mt-2 {{element[0]?.translations[0].title}}
                div.mt-4(v-html="textdata"  v-if="element[0]")
                .user
                    span
                        img(src="@/assets/images/clock.png", alt="").ms-2
                        span {{creatdate(element[0]?.date_created_func) }}
                    span.me-4
                        img(src="@/assets/images/user.png", alt="").ms-2
                        span {{element[0]?.category.user_created.first_name + " " + element[0]?.category.user_created.first_name }}
            .adv    
                .img
                    img(:src="'https://board.humm.world/assets/' + banner2.id")
                .img
                    img(:src="'https://board.humm.world/assets/' + banner3.id")
        .section3.main-margin
            Advertisevue(ad="1")
        .section2.main-margin
            .head.d-flex.justify-content-between
                h2 Food
                nuxt-link(to="/food"):  Cardbutton(color="light") Show More 
            Food(:limit=8 )   

</template>

<script lang="ts" setup>
const route = useRoute();
const { data } = useAsyncGql({
  operation: "getfood"
});
let textdata = ref("");
let element = ref("");

const { data: posters } = await useAsyncGql({
  operation: "posters"
});
const advposters = posters.value.posters.translations[1];
const banner2 = {
  id: advposters.normal2_cover.id,
  title: advposters.normal2_title,
  url: advposters.normal2_url
};
const banner3 = {
  id: advposters.normal_cover.id,
  title: advposters.normal_title,
  url: advposters.normal_url
};

onBeforeMount(() => {
  const foodarr = data?.value?.Article;
  console.log("foodarr", foodarr);

  const item = foodarr?.filter(e => {
    return e.slug === route.params.slug;
  });
  element.value = item;
  console.log("element", element.value[0]);
  const title = item[0]?.translations[0].title;
  const articles = item[0]?.category.articles;
  const htmldata = articles?.filter(e => e.translations[0]?.title === title);

  const htmltext = htmldata[0]?.translations[0].content;
  textdata.value = htmltext;
  console.log(textdata.value);
});

function creatdate(item) {
  return `${item?.year}-${item?.month}-${item?.day} `;
}
</script>

<style lang="scss" scoped>
// .head {
//   height: 300px;
//   img {
//     width: 100%;
//     height: 100%;
//     object-fit: cover;
//   }
// }
.content {
  .user {
    span {
      img {
        width: 20px;
      }
      color: #777;
    }
  }
  @media (max-width: 992px) {
    flex-direction: column;
    .adv {
      flex-direction: row !important;
    }
  }
  gap: 30px;
  .recipe {
    width: 70%;
  }
  .adv {
    flex: 1;
    gap: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;

    .img {
      img {
        height: auto;
        width: 100%;
      }
    }
  }
}
</style>