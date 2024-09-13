# FormKit HoneyPot

Prevent spam in your Vue.js + FormKit applications.

[Learn how honeypot fields work](https://dev.to/felipperegazio/how-to-create-a-simple-honeypot-to-protect-your-web-forms-from-spammers--25n8)

```
npm i formkit-honeypot vue @formkit/vue
```

```html
<script setup lang="ts">
  import { ref } from 'vue'
  import FormKitHoneypot from 'formkit-honeypot'

  const honeypot = ref<InstanceType<typeof FormKitHoneypot>>()(before)
  // const honeypot = useTemplateRef() (Vue 3.5 +)

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

## Props

- `name` - should be something bots are tempted to fill in (not something they'd want to avoid like "honeypot") - defaults to website. If you are collecting a "website" field on your form for real, you'll want to change this, otherwise the default is fine.

- `ref` - not really a prop. Enables template refs. [See Vue docs for more info](https://vuejs.org/guide/essentials/template-refs.html)
