<template lang="pug">
.show 
    .container 
        .head.py-5(v-if="myelement[0]")
            img(:src="'https://board.humm.world/assets/' + checkdata(myelement[0]).cover.id" )
            .content.w-100.text-center
                h1.mt-5(v-if="myelement[0]") {{checkdata(myelement[0]).title}}
                p.mt-3(v-if="myelement[0]") {{checkdata(myelement[0]).description}}
                div
                    img(src="@/assets/images/video.png" style="width:50px").me-2    
                    span.me-2 {{myelement[0]?.all_episodes_func.count}} eposide
        Eposides(:element="dataeposides" v-if="dataeposides?.all_episodes" )
        //- .section2.main-margin
        //-     .container
        //-         Advertisevue(ad="1")   
</template>
    
<script lang="ts" setup>
const route = useRoute();
const { data } = useAsyncGql({
  operation: "Shows"
});
let mytextdata = ref("");
let myelement = ref("");


let dataeposides = ref("");



const { data:show} =await useAsyncGql({
  operation: "eposide",
  variables: {  slug: route.params.slug }
});

dataeposides.value = show.value?.shows[0];
console.log("epo", dataeposides.value);

onBeforeMount(() => {
  const show = data?.value?.shows;
  console.log("show", show);

  const item = show?.filter(e => {
    return e.slug === route.params.slug;
  });
  myelement.value = item;
  console.log(myelement.value);
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
.head {
  p {
    font-size: 1.5rem;

    font-weight: 600;
  }
  span {
    font-size: 1.2rem;
  }
  img {
    width: 100%;
    height: auto;
    object-fit: cover;
  }
}
.img {
  width: 40%;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
}
.data {
  span {
    img {
      width: 20px;
    }

    font-size: 15px;
  }
  width: 60%;
  flex: 1 1 auto;
  p {
    width: 80%;
    font-weight: 800;
  }
  .clock {
    span {
      font-size: initial;
    }
  }
}
</style>