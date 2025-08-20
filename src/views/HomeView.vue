<script setup>
import ProductList from '@/components/ProductList.vue'
import CartList from '@/components/CartList.vue'
import { ref } from 'vue'

const data = [
  {
    id: 1,
    title: '耳罩式藍牙耳機',
    content: '舒適配戴，支援降噪技術',
    price: 2490,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 2,
    title: '耳罩式彩虹耳機',
    content: '舒適配戴，支援降噪技術',
    price: 1380,
    imgUrl:
      'https://plus.unsplash.com/premium_photo-1679913792906-13ccc5c84d44?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 3,
    title: '時尚藍芽耳機',
    content: '舒適配戴，支援降噪技術',
    price: 7990,
    imgUrl:
      'https://images.unsplash.com/photo-1631281637549-fb740447b4ee?q=80&w=1247&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 4,
    title: '機械式鍵盤',
    content: '紅軸機械鍵盤，打字手感極佳',
    price: 1890,
    imgUrl:
      'https://images.unsplash.com/photo-1595044426077-d36d9236d54a?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 5,
    title: '無線滑鼠',
    content: '靜音按鍵設計，長效電池',
    price: 890,
    imgUrl:
      'https://images.unsplash.com/photo-1615663245857-ac93bb7c39e7?q=80&w=765&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
]

const productList = ref(data)
const cartList = ref([])

const addCart = (product) => {
  const cartItem = cartList.value.find((i) => i.id === product.id)
  if (cartItem) {
    cartItem.qty += 1
  } else {
    cartList.value.push({
      ...product,
      qty: 1,
    })
  }
}

const removeItem = (itemId) => {
  cartList.value = cartList.value.filter((i) => i.id !== itemId)
}
</script>

<template>
  <div id="app" class="container py-4">
    <div class="row">
      <ProductList :productList="productList" :addCart="addCart" />
      <CartList :cartList="cartList" @removeItem="removeItem" />
    </div>
  </div>
</template>

<style scoped>
body {
  background: #f2f2f2f2;
}
</style>
