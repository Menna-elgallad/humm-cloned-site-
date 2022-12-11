<template lang="pug">
.hummform   
    form(@submit.prevent="check()").mt-4
        .fields.d-flex     
            .inputs     
                label.my-3(for="name") الاسم بالكامل 
                .input 
                    input.p-2(id="name" type="text" v-model="username" :class="{'error': nameerror } , color")
                    span(v-if="nameerror"): img(src="@/assets/images/error.png", alt="")
                p(v-if="nameerror") {{nameerror}}
            .inputs     
                label.my-3(for="phone") رقم الهاتف
                .input
                    input.p-2(id="phone" type="phone" v-model="phone" :class="{'error': phoneerror} , color")
                    span(v-if="phoneerror"): img(src="@/assets/images/error.png", alt="")

                p(v-if="phoneerror") {{phoneerror}}

        .fields.d-flex     
            .inputs     
                label.my-3(for="email") البريد الالكتروني
                .input
                    input.p-2(id="email" type="email" v-model="email" :class="{'error': emailerror }, color")
                    span(v-if="emailerror"): img(src="@/assets/images/error.png", alt="")

                p(v-if="emailerror") {{emailerror}}

            .inputs     
                label.my-3(for="us") كيف سمعت عنا
                input.p-2(id="us" type="text" v-model="us" :class="color")
        .fields   
            .inputs     
                label.my-3(for="message") الرسالة
                .input
                    textarea.p-5(id="message"  v-model="message" :class="{'error': messageerror }, color")
                    span(v-if="messageerror"): img(src="@/assets/images/error.png", alt="")

                p(v-if="messageerror") {{messageerror}}

        Cardbutton.mt-3(:color="color" @click="check()") ارسال 

</template>

<script lang="ts" setup>
const props= defineProps({
    color  : String
}) ; 
let username = ref("");
let phone = ref("");

let email = ref("");

let message = ref("");
let nameerror = ref("")
let emailerror = ref("")
let phoneerror = ref("")
let messageerror = ref("")

function check(){
    nameerror.value = "" ; 
    emailerror.value = "" ; 
    phoneerror.value = "" ; 
    messageerror.value = "" ; 

    if (!username.value){
        nameerror.value = "ادخل الاسم بالكامل"
    }
    if (!email.value){
        emailerror.value = "ادخل بريدك الالكتروني"
    }
    if (!phone.value){
        phoneerror.value = "ادخل رقم الهاتف"
    }
    if (!message.value){
        messageerror.value = "ادخل الرسالة المرسلة"
    }
    
}
</script>

<style lang="scss" scoped>
.fields{
    .input{
        position: relative;
        span{
            position: absolute;
            left: 8px;
            top: 8px;
        }
    }
    gap: 20px;
    p{
        color: red;
    }
    .inputs{
    width: 100%;

    label{
        display: block;
    }
    input ,textarea{
    &.dark{
    border:1px solid  white;

    }
    
    &.light{
    border:1px solid  black;

    }
    &.error{
        border-color: #ff80a2;
        outline: none !important;
    }
    &:focus{
        border-color: #ff80a2;
        box-shadow: 0 0 0 0.25rem #ff004540;
        outline: none !important;

    }
    background-color: transparent;
    width: 100%;
    transition: all 0.3s ease-out;
    color: white;
}
}
}


</style>