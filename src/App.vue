<script setup lang="ts">
import { ref } from 'vue'
import FormKitHoneypot from './components/FormKitHoneypot.vue'

const honeypot = ref()

function formHandler(form) {
  if (!honeypot.value?.isSpam()) {
    console.log('submitting')
  } else {
    console.log('spam detected')
  }
}
</script>

<template>
  <FormKit type="form" @submit="formHandler">
    <FormKit type="text" name="name" label="Name" />
    <FormKitHoneypot ref="honeypot" />
  </FormKit>
</template>
