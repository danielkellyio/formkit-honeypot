<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
const props = withDefaults(
  defineProps<{
    name?: string
  }>(),
  {
    name: 'website'
  }
)

const honeypot = ref<HTMLDivElement | undefined>()
const input = computed(() => ({
  type: 'honeypot',
  schema: [
    {
      $el: 'input',
      attrs: {
        type: 'text',
        name: props.name
      }
    }
  ]
}))

defineExpose({
  isSpam() {
    return !!honeypot.value?.querySelector('input')?.value
  }
})
onMounted(() => {
  document.head.appendChild(document.createElement('style')).textContent = `
    .xyz-dsajasohwpejr0234hjsr-0afd {
      opacity: 0 !important;
      z-index: -1 !important;
      position: fixed !important;
      top: -1000px !important;
      left: -1000px !important;
    }
  `
})
</script>
<template>
  <div class="xyz-dsajasohwpejr0234hjsr-0afd" ref="honeypot">
    <FormKit :type="input" :name="name" />
  </div>
</template>
