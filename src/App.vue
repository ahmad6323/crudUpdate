<script >
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import  navbar from './components/navbar.vue'
import addProduct from "@/components/addProduct.vue";
export default {
  name:'App',
  components:{
    navbar, addProduct
  }
}
</script>
<template>
  <navbar />
  <addProduct />
</template>

