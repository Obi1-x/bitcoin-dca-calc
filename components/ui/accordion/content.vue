<!-- Accordion Content -->
<template>
  <div
    v-show="openIndex === index"
    class="overflow-hidden text-sm transition-all"
  >
    <div class="pb-4 pt-0">
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
defineProps({
  index: Number,
  openIndex: Number,
});
</script>