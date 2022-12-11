<template lang="pug">
.about 
    .container 
        .headimg 
            .content
                .head 
                    h1 About Humm
                .text 
                    span HUMM is a world for all things food and lifestyle — here, you’ll find everything you need to make amazing food, to find incredible gifts, to pamper yourself, and to uplift your home. A lot of our products and bundles are imported, so you won’t find them anywhere else — stay tuned as more and more products come to humm.world every day, from all over the world.  
                    img(src="@/assets/images/shape.png")

    .section8.main-margin
        .container
            .head.d-flex.justify-content-between
                h2 Brands advirtising with us 
                Cardbutton(color="light") Show More 
            Brands    
    .section3.main-margin
        .container
            Advertisevue(ad="1")
</template>

<script lang="ts" setup>
</script>

<style lang="scss" scoped>
.about {
  .headimg {
    background-image: url("@/assets/images/aboutimg.png");
    padding: 18rem 0;
    width: 100%;
    background-size: cover;
    background-position: 50%;
    position: relative;
    .content {
      position: absolute;
      display: flex;
      justify-content: space-evenly;
      top: 50%;
      transform: translateY(-50%);
      z-index: 100;
      @media (max-width: 990px) {
        flex-direction: column;
        justify-content: center;
        align-items: center;
        .text {
          width: 90% !important;
        }
      }
      .head {
        color: white;
      }
      .text {
        position: relative;
        width: 40%;
        background-color: white;
        padding: 3rem 2rem;
        position: relative;
        img {
          position: absolute;
          left: -19px;
          top: -13px;
          width: 13%;
        }
      }
    }
    &::after {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.438);
    }
  }
}
</style>