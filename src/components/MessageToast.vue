<script setup>
import { inject } from 'vue'

const { messageText, isShow } = inject('message', 'isShow')
console.log(messageText)

const closeToast = () => {
  isShow.value = false
}
</script>

<template>
  <div v-show="isShow">
    <div
      class="position-fixed top-0 end-0 p-3"
      style="z-index: 1050"
      v-for="message in messageText"
      :key="message.id"
    >
      <div
        class="toast show align-items-center text-white border-0"
        :class="message.status ? 'bg-success' : 'bg-danger'"
      >
        <div class="d-flex">
          <div class="toast-body">{{ message.text }}</div>
          <button
            type="button"
            class="btn-close btn-close-white me-2 m-auto"
            @click="closeToast"
          ></button>
        </div>
      </div>
    </div>
  </div>
</template>
