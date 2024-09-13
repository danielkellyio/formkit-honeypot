<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    name?: string;
  }>(),
  {
    name: "fax",
  }
);

const honeypot = ref<HTMLDivElement | undefined>();
const input = computed(() => ({
  type: "honeypot",
  schema: [
    {
      $el: "input",
      attrs: {
        type: "text",
        name: props.name,
      },
    },
  ],
}));

defineExpose({
  isSpam() {
    return !!honeypot.value?.querySelector("input")?.value;
  },
});
</script>
<template>
  <div class="xyz" ref="honeypot">
    <FormKit :type="input" :name="name" />
  </div>
</template>
<style scoped>
.xyz {
  opacity: 0 !important;
  z-index: -1 !important;
  position: fixed !important;
  top: -1000px !important;
  left: -1000px !important;
}
</style>
