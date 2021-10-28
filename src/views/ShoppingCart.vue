<template>
  <div class="home container">
    <div class="row">
      <div class="col-md-8 pt-5">

       <CartItem v-for="product in cart" :product="product" :key="product.id" />
        
      </div>
      <div class="col-md-4 pt-5">
        
        <Cart />
      </div>
      
    </div>
  </div>
</template>

<script>

import CartItem from "../components/CartItem.vue";
import Cart from "../components/Cart.vue";
import { computed, inject } from "vue";
import {useStore} from "vuex";

export default {
  name: 'ShoppingCart',
  components: {
    CartItem,
    Cart
  },
  setup(){
    const store2 = useStore();
    const store = inject('CAPIStore');

    let cart = computed(function () {
        return store.state.cart
    });

    return {
        cart
    }
  }
}
</script>
