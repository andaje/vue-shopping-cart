<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div :key="product.id" class="col-md-6" v-for="product in products">
            <product :isInCart="inCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></product>
          </div>
         
          
        </div>
       
      
      </div>
      <div class="col-md-5 my-5">
        <cart v-on:remove-from-cart="removeFromCart($event)" :items="cart"></cart>
      </div>
    </div>
  </div>
</template>

<script>
import products from '@/products.json';
import Product from '@/components/Product.vue';
import Cart from '@/components/Cart.vue';

export default {
  name: 'app',
    data(){
      return{
          products,
          cart:[]
      }
    },
    components:{
        Product,
        Cart
    },
    methods:{
      addToCart(product){
         this.cart.push(product)
      },
        inCart(product){
          const item = this.cart.find(item => item.id === product.id)
            
            if(item){
                return true
            }
            return false
        },
        removeFromCart(product){
          this.cart = this.cart.filter(item => item.id !== product.id)
        }
    }
    
   
  
}
</script>

<style>
body{
  background-color:lightblue;
}
</style>
