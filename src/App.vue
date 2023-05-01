<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>