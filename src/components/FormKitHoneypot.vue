<script setup lang="ts">
import { ref, computed } from 'vue'
import { FormKit } from '@formkit/vue'
const props = withDefaults(
  defineProps<{
    name?: string
  }>(),
  {
    name: 'website'
  }
)

const honeypot = ref<HTMLDivElement | undefined>()
const input = computed(
  () =>
    ({
      type: 'honeypot',
      schema: [
        {
          $el: 'input',
          attrs: {
            type: 'text',
            name: props.name,
             autocomplete: "off"
          }
        }
      ]
    }) as unknown as 'text'
)

defineExpose({
  isSpam() {
    return !!honeypot.value?.querySelector('input')?.value
  }
})

const style = `opacity: 0 !important; z-index: -1 !important; position: fixed !important; top: -1000px !important; left: -1000px !important;`
</script>
<template>
  <div :style="style" ref="honeypot">
    <FormKit :type="input" :name="name" />
  </div>
</template>
