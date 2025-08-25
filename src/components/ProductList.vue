<script setup>
// import { defineProps } from 'vue'

defineProps(['productList', 'addCart'])
</script>

<template>
  <div class="col-md-8">
    <h2 class="mb-3">商品列表</h2>
    <div class="row">
      <div class="col-md-4 mb-4" v-for="product in productList" :key="product.id">
        <div class="card h-100">
          <img :src="product.imgUrl" class="card-img-top" />
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ product.title }}</h5>
            <p class="card-text">{{ product.content }}</p>
            <p class="fw-bold text-primary">$ {{ product.price }}</p>
            <button class="btn btn-success w-100 mt-auto" @click="addCart(product)">加入購物車</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card-img-top {
  height: 150px;
  object-fit: cover;
}
</style>
