<template>
  <div class="order-terms">
    <button @click="selectTerm('salary')" class="p-2 border-2 rounded border-green-500 mr-4 hover:bg-green-500 hover:text-white">Order by salary</button>
    <button @click="selectTerm('title')" class="p-2 border-2 rounded border-green-500 mr-4 hover:bg-green-500 hover:text-white">Order by title</button>
    <button @click="selectTerm('location')" class="p-2 border-2 rounded border-green-500 hover:bg-green-500 hover:text-white">Order by location</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import OrderTerm from '@/types/OrderTerm'

export default defineComponent({
  setup(props, context) {
    const term = ref<OrderTerm>('salary')

    const selectTerm = (selectedTerm: OrderTerm) => {
      term.value = selectedTerm

      context.emit('selectedTerm', selectedTerm)
    }

    return {
      term,
      selectTerm
    }
  },
})
</script>
