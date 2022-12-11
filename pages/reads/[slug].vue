<template lang="pug">
.article 
    .container(style="direction:rtl")
      .d-flex.content.mt-5
            .recipe
                h2.fw-bolder.mt-2(v-if="myelement[0]") {{myelement[0].translations[0].title}}
                div.mt-4.html(v-html="mytextdata"  v-if="myelement[0]")
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
              nuxt-link(to="/reads"):  Cardbutton(color="light") Show More 
          Articles(:limit=2 )   
  
</template>

<script lang="ts" setup>
  const route = useRoute();
  const { data } = useAsyncGql({
    operation: "getArticles" 
  });
  let mytextdata = ref("");
  let myelement = ref("");

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
    const article = data?.value?.Article;
    console.log("article", article);

    const item = article?.filter(e => {
      return e.slug === route.params.slug;
    });
    myelement.value = item;
  
    const htmltext = item[0]?.translations[0].content;
    mytextdata.value = htmltext;
    console.log("text",mytextdata.value);
    console.log("element",myelement.value);
  });

  function creatdate(item) {
    return `${item?.year}-${item?.month}-${item?.day} `;
  }

</script >

<style lang="scss" scoped>
.content {

  @media (max-width: 992px) {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .recipe{
      width: 100% !important;
    }
    .adv {
      flex-direction: row !important;
    }
  }
  gap: 30px;
  .recipe {
    width: 60%;
  }
  .adv {
    flex: 1;
    gap: 20px;
    display: flex;
    flex-direction: column;


    .img {
      img {
        height: auto;
        width: 100%;
      }
    }
  }
}
</style>