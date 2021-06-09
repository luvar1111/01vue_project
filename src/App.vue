<template>
  <ul>
    <li v-for="(item,i) in product" :key="i">
      {{product[i].title}}
    </li>
  </ul>

  <test />
</template>

<script>
import vdata from './data.js'
import banner from './components/banner.vue'


export default {
  name: 'App',
  data(){
    return{
      product:vdata,
    }
  },
  components:{
    test:banner
  }
}
</script>

<style>
* {margin:0; padding:0;}
li {list-style:none}
</style>
