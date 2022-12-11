<template lang="pug">
.section1 
    .row
        .item.col-md-6.mt-3(v-for="eposide in element?.all_episodes" )
            nuxt-link(:to="'/shows/'+element.slug+'/'+ eposide.slug")
                 Card(color="light" ).d-flex
                    .data.me-3(style="direction:rtl").mt-3
                        span.rounded-pill.border.border-dark.p-2.mt-2.d-inline-block.px-3 {{checkdata(element).title}}
                        h4.fw-bolder.mt-2 {{eposide?.translations[0]?.title}}
                        div.d-flex.align-items-center.py-1.clock
                            img(src="@/assets/images/clock.png", alt="")
                            span.me-1 {{creatdate(eposide?.date_created_func)}}
                    .img
                        img(:src="'https://board.humm.world/assets/'+ eposide?.translations[0].cover.id")    
</template>

<script lang="ts" setup>
const props = defineProps({
  element: Object,
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