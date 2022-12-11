<template lang="pug">
.eposide.mt-4
    .content   
      .container(style="direction:rtl")
          .head.py-5
            iframe(width="100%" height="700px" :src="'https://www.youtube.com/embed/'+element[0]?.video" v-if="element[0]")

          .d-flex.content
              .recipe
                  nuxt-link(:to="'/shows/'+myitem?.slug"): span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3.mt-3 {{myitem?.slug?.split("-").join(" ")}}
                  h2.fw-bolder.mt-2 {{element[0]?.translations[0].title}}
                  p.mt-4(v-html="element[0]?.translations[0].content"  v-if="element[0]" )
                  .user
                      span
                          img(src="@/assets/images/clock.png", alt="").ms-2
                          span {{creatdate(element[0]?.date_created_func) }}
                      
              .adv    
                  .img
                      img(:src="'https://board.humm.world/assets/' + banner2.id")
                  .img
                      img(:src="'https://board.humm.world/assets/' + banner3.id")
          .section2.main-margin
              Advertisevue(ad="1")
          .section3.main-margin
              .head.d-flex.justify-content-between
                  h2 More Eposides
                  nuxt-link(:to="'/shows/'+$route.params.slug"):  Cardbutton(color="light") Show More 
              Eposides(:element="dataeposides" v-if="dataeposides?.all_episodes" )
      .section5.main-padding2.main-margin
        .container
            .head.d-flex.justify-content-between
                h2 Shows 
                nuxt-link(:to="'/shows'"): Cardbutton(color="dark") Show More 
            Shows(:limit=4 color="dark") 
</template>

<script lang="ts" setup>
const route = useRoute();
const { data } = useAsyncGql({
  operation: "Shows"
});
let mytextdata = ref("");
let element = ref("");
let myitem = ref("");
console.log(route.params.slug);
console.log(route.params.eposide);

let dataeposides = ref("");

const { data:show} =await useAsyncGql({
  operation: "eposide",
  variables: { limit :4 , slug: route.params.slug }
});

dataeposides.value = show.value?.shows[0];
console.log("epo", dataeposides.value);



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
  const show = data?.value?.shows;
  console.log("show", show);

  const item = show?.filter(e => {
    return e.slug === route.params.slug;
  });
  myitem.value = item[0];

  const myelement = item[0].all_episodes?.filter(e => {
    return e.slug === route.params.eposide;
  });
  element.value = myelement;
});

function checkdata(item) {
  if (item.translations[0]?.cover === null) {
    console.log("from 1");
    return item.translations[1];
  } else {
    console.log("from 2");
    return item.translations[0];
  }
}
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
.section5 {
  background-color: black;
  color: white !important;
}
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