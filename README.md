# FormKit HoneyPot

Prevent spam in your Vue.js + FormKit applications.

```
npm i formkit-honeypot
```

```html
<script setup lang="ts">
  import FormKitHoneypot from "formkit-honeypot";

  const honeypot = useTemplateRef();

  function formHandler(form) {
    if (!honeypot.value?.isSpam()) {
      // submit the form only for humans
    }

    // show your confirmation to bots and people alike
  }
</script>

<template>
  <FormKit type="form" @submit="formHandler">
    <!-- Other legit fields here...-->
    <FormKitHoneypot
      name="some convincing field name that isn't on your form. Default is 'website'"
      ref="honeypot"
    />
  </FormKit>
</template>
```
