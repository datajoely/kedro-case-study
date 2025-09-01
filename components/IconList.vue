<template>
  <ul class="list-none space-y-1">
    <li v-for="(item, index) in items" :key="index" class="flex items-center gap-2">
      <component :is="item.icon" :class="`${color} flex-shrink-0`" />
      <span v-html="item.text"></span>
    </li>
  </ul>
</template>

<script setup>
defineProps({
  items: {
    type: Array,
    required: true
  },
  color: {
    type: String,
    default: 'text-blue-500'
  }
})
</script>