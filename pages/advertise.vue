<template lang="pug">
.advertise 
    .container(style="direction:rtl") 
        .section1.d-flex.align-items-center.justify-content-between.main-margin
            .img
                img(src="https://humm.world/images/main/2.png")
            .text 
                h2 اعرض شركتك ومنتجاتك لملايين من خلال الإعلان على موقعنا    
                p.mt-3 همم عندها تقريبًا 2 مليون متابع وبتكبر يوم عن يوم! كلهم بييجوا هنا علشان يتعلموا ويبتكروا ويحتفلوا بحب الأكل وده اللي بيخلينا أحسن مكان تعلن فيه. بغض النظر عن حجم شركتك، دايمًا فيه مكان ليك. كون جزء من عالم همم.
                p اختار أكتر من مكان في موقع همم مع اختيار وجود مقالات مخصصة ومراجعة تفصيلية للمنتجات وصور. ابعتلنا دلوقتي!
        .section2.main-margin    
            h2 ليه تعلِن معانا؟
            .row.mt-4
                .col-lg-3.col-md-6.mt-3
                    .content.border.border-dark.p-4.px-5
                        img(src="@/assets/images/shape1.svg")
                        h2.mt-3 هتلاقي الجمهور اللي يهمك.
                        p.mt-3 بنعمل المحتوى على حسب اهتمامات مشاهدينا وسلوكهم وموقعهم وأكتر. وصل شركتك بالناس اللي بتغير العالم بالقيم والسلوكيات اللي بتغير العام.
                .col-lg-3.col-md-6.mt-3
                    .content.border.border-dark.p-4.px-5
                        img(src="@/assets/images/shape2.svg")
                        h2.mt-3 اختار من بين مجموعة من الأماكن والبانرات.
                        p.mt-3 تقدر تختار المكان اللي تحب تعلن فيه في أي مكان على موقعنا أو بالأخص في المقالات
                .col-lg-3.col-md-6.mt-3
                    .content.border.border-dark.p-4.px-5
                        img(src="@/assets/images/shape3.svg")
                        h2.mt-3 اشتغل مع صناع محتوى همم
                        p.mt-3 على حسب شركتك واحتياجاتها، تقدر تشتغل مع صناع محتوى همم، ويعملوا محتوى خاص ومراجعة لمنتجاتك بالتفصيل. اسألنا على أنواع الاعلانات اللي بنقدمها.
                .col-lg-3.col-md-6.mt-3
                    .content.border.border-dark.p-4.px-5
                        img(src="@/assets/images/shape4.svg")
                        h2.mt-3 تكون راعي لفيديوهاتنا:
                        p.mt-3 ممكن تنقل شركتك خطوة قدام بإنك ترعى فيديو على صفحتنا. همم عندها 2 مليون متابع تقريبًا وشراكات متعددة ومشاهدات بأكتر من 230 مليون على كل مواقع التواصل الإجتماعي. منتجاتك انت كمان هتتشاف ملايين المرات!
        .section3.main-margin.p-5
            h2 اعلن مع همم.
            Hummform(color="dark")


</template>

<script lang="ts" setup>

</script>

<style lang="scss" scoped>
.advertise{
    .container{
        .section1{
            gap: 30px;
            .img{
                img{
                    width: 100%;
                    object-fit: cover;
                    height: auto;
                }
            }
            .text{
                font-size: larger;
                width: 50%;
            }
            @media (max-width:992px) {
                flex-direction: column;
                justify-content: center !important;
                .text{
                    width: 100%;
                    margin-top: 2rem;
                }
            }
        }
        .section2{
            .row{
                height: auto;
                .content{
                    height: 100%;
                    
                }

            }
        }
        .section3{
            background-color: black;
            color: white;
        }
    }
}
</style>