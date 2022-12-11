<template lang="pug">
.contact 
    .container 
        .content.d-flex(style="direction:rtl")
            .first  
                .img
                    img(src="@/assets/images/contact.png")
                .text 
                    h1 شاركونا استفساراتكم واقتراحاتكم
                    .links.mt-3
                        a(href="mailto:hi@humm.world")
                            img(src="@/assets/images/letter.png") 
                            h3 Hi@humm.world
                        a
                            img(src="@/assets/images/ring.png") 
                            h3 +20 101 987 0053
            .humform.w-50
                Hummform(color="light")    
</template>

<script lang="ts" setup>

</script>

<style lang="scss" scoped>
.content{
    @media (max-width:992px) {
        flex-direction: column;
        .humform{
            width: 100% !important;
        }
        .text{
            h1{
                font-size: 2rem !important; 
            }
            h3{
                font-size: 1rem !important;
            }
        }
   
    }
    .first{
        position: relative;
        
        
        img{
            width: 100%;
        }
        .text{

            position: absolute;
            color: white;
            top: 19%;
            width: 50%;
            right: 32%;
            a{
                color: white  !important; 
                display: flex;
                gap: 10px;
                
                &:hover{
                    color: red !important;
                }
                img{
                    width: 30px;
                }
                
            }
        }
    }
}
</style>