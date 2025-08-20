<script setup>
import { defineProps, defineEmits } from 'vue'
import { computed } from 'vue'

const props = defineProps(['cartList'])
const emit = defineEmits(['removeItem'])

const cartTotal = computed(() => {
  return props.cartList.reduce((prev, item) => prev + item.price * item.qty, 0).toLocaleString()
})
</script>

<template>
  <div class="col-md-4">
    <h2 class="mb-3">購物車</h2>
    <ul class="list-group mb-3">
      <li
        class="list-group-item d-flex justify-content-between align-items-center"
        v-for="cartItem in cartList"
        :key="cartItem.id"
      >
        <div>
          <h6 class="my-0">{{ cartItem.title }}</h6>
          <small class="text-muted">數量：{{ cartItem.qty }}</small>
        </div>
        <div>
          <span class="text-muted">${{ cartItem.price }}</span>
          <button
            class="btn btn-sm btn-outline-danger ms-2"
            @click="emit('removeItem', cartItem.id)"
          >
            移除
          </button>
        </div>
      </li>
    </ul>
    <div class="text-end fw-bold">總金額 : ${{ cartTotal }}</div>
  </div>
</template>
