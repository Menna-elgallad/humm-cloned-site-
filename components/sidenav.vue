<template lang="pug">
.sidenav
    .container
        .img.w-100(@click="$emit('close')")
            svg(xmlns="http://www.w3.org/2000/svg" width="30.135" height="38.135" viewBox="0 0 38.135 38.135").float-end.m-3
                g(id="Group_21402" data-name="Group 21402" transform="translate(-333.336 -30)")
                    path(id="close-filled" d="M21.318,2.25A18.95,18.95,0,0,0,2.25,21.318,18.95,18.95,0,0,0,21.318,40.385,18.95,18.95,0,0,0,40.385,21.318,18.95,18.95,0,0,0,21.318,2.25Zm7.355,28.6L21.318,23.5l-7.355,7.355-2.179-2.179,7.355-7.355-7.355-7.355,2.179-2.179,7.355,7.355,7.355-7.355,2.179,2.179L23.5,21.318l7.355,7.355Z" transform="translate(331.086 27.75)" fill="#fff")
        ul.py-5
            li.py-3.px-5: nuxt-link(to="/" @click="$emit('close')") Home
            li.py-3.px-5: nuxt-link(to="/food" @click="$emit('close')") Food 
            li.py-3.px-5: nuxt-link(to="/shows" @click="$emit('close')") Shows
            li.py-3.px-5: nuxt-link(to="/reads" @click="$emit('close')") Read
            li.py-3.px-5: nuxt-link(to="/press" @click="$emit('close')") Press 
            li.py-3.px-5: nuxt-link(to="/about" @click="$emit('close')") About Us 
            li.py-3.px-5: nuxt-link(to="/contact" @click="$emit('close')") Contact Us 
            li.py-3.px-5: nuxt-link(to="/advertise" @click="$emit('close')") Advertise With Us 
            li.py-3.px-5: nuxt-link(to="/" @click="$emit('close')") Subscribe
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.sidenav {
  z-index: 1000;

  position: fixed;
  top: 0;
  left: 0;
  background-color: black;
  min-width: 20%;
  height: 100vh;
  .img {
    cursor: pointer;
    width: 80px;
    svg {
      &:hover {
        path {
          fill: red !important;
        }
      }
    }
  }
  li {
    a {
      color: white;
      font-size: 1.8rem;
      font-weight: 700;
      &:hover {
        color: red !important;
      }
    }
  }
}
</style> 