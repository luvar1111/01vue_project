<template>
  <my-banner/>

  <!-- <div class="black-bg" v-if="proView == true">
    <div class="white-bg">
      <img v-bind:src="product[proNum].image">
      <div>{{product[proNum].title}}</div>
      <div>{{product[proNum].price}}</div>
      <div>{{product[proNum].content}}</div>
      <button v-on:click="proView=false">닫기</button>
    </div>
  </div> -->
  <!-- <div class="start" :class="{end:proView}"> -->
    <transition name="show">
    <modal :product="product" :proView="proView" :proNum="proNum" @modalClose="proView=false"/>
    </transition>
  <!-- </div> -->
  

  <!-- <ul class="view">
    <li v-for="(item,i) in product" :key="i">
      <img v-bind:src="product[i].image">
      <div>{{product[i].title}} <span v-on:click="proView=true;proNum=i">[상세보기]</span></div>
      <div>{{product[i].price}}</div>
    </li>
  </ul> -->
  <product :product="product[i]" v-for="(item,i) in product" :key="i" @modalOpen="proView=true;proNum=$event"/>
  
  
</template>

<script>
import vdata from './data.js'
import banner from './components/banner.vue'
import modal from './components/modal.vue'
import product from './components/product.vue'


export default {
  name: 'App',
  data(){
    return{
      proNum:0,
      proView:false,
      product:vdata,
    }
  },
  components:{
    'my-banner':banner,
    modal:modal,
    product:product,
  }
}
</script>

<style>
* {margin:0; padding:0;}
li {list-style:none}
img {width:100%}
.view li {margin-bottom:20px;}
.black-bg {position: fixed; width: 100%; height: 100%; background: rgba(0,0,0,0.5); top: 0;
           display:flex; justify-content: center; align-items: center;}
.white-bg {width: 80%; background: #fff; border-radius:5px; padding: 20px;}
.start {opacity:0; transition:1s}
.start.end {opacity:1}

.show-enter-from, .show-leave-to {opacity:0; transform:translateY(-1000px)}
.show-enter-active, .show-leave-active {transition:1s}
.show-enter-to, .show-leave-from {opacity:1; transform:translateY(0)}
</style>
