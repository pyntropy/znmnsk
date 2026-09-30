<script setup>
defineProps({
  label: {
    type: String,
    default: 'Button'
  }
})
</script>

<template>
  <button @click="$emit('click')">{{ label }}</button>
</template>

<style scoped>
button {
  padding: 0.5rem 1rem;
  cursor: pointer;
}
</style>
