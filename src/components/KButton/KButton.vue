<template>
  <button
    :class="[
      'inline-flex items-center justify-center font-medium transition border border-gray-300',
      sizeClass,
    ]"
    @click="handleClick"
  >
    {{ label }}
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  /** Button size */
  size?: 'small' | 'medium' | 'large'
  label: string
}>()

const emit = defineEmits<{
  (eventName?: 'click', event?: MouseEvent): void
}>()

const sizeClass = computed(() => {
  switch (props.size) {
    case 'small':
      return 'px-2 py-1 text-sm rounded'
    case 'large':
      return 'px-6 py-3 text-lg rounded-lg'
    default:
      return 'px-4 py-2 text-base rounded-md'
  }
})

const handleClick = (event?: MouseEvent) => {
  emit('click', event)
}
</script>
