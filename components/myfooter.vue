<template lang="pug">
.footer.main-margin
    .container.py-5
        .sec1.d-flex.justify-content-between.align-items-center
            Cardbutton(color="light") subscribe 

            ul.d-flex.justify-content-between
                li.fw-bold.ps-4: nuxt-link(to="/about") About US 
                li.fw-bold.ps-4: nuxt-link(to="/press") News 
                li.fw-bold.ps-4: nuxt-link(to="/advertise") Advertise 
                li.fw-bold.ps-4: nuxt-link(to="/contact") Contact     
            .logos
                .d-flex
                    ul.d-flex
                        li.ps-3:   img(src="@/assets/images/social/facebook.png", alt="")
                        li.ps-3:   img(src="@/assets/images/social/insta.png", alt="")
                        li.ps-3:   img(src="@/assets/images/social/twitter.png", alt="")
                        li.ps-3:   img(src="@/assets/images/social/youtube.png", alt="")
        .sec2.d-flex.justify-content-center.align-items-center.mt-3
            img(src="@/assets/images/footerlogo.png").py-3
            ul.d-flex.justify-content-center
                li.me-3.small: a Shipping Policy   
                li.me-3.small: a Returning Policy
                li.me-3.small: a Privacy Policy
                li.me-3.small: a Rules      
            p.small All rights reserved for Humm 2022

            

</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.footer {
  .container {
    border-top: 1px solid black;
    ul {
      flex-wrap: wrap;
      li {
        img {
          width: 20px;
        }
      }
    }
    .sec1 {
      @media (max-width: 990px) {
        flex-direction: column;
        justify-content: center;
        gap: 20px;
      }
    }
  }
  .sec2 {
    flex-direction: column;
    gap: 20px;
  }
}
</style>