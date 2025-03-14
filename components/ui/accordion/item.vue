<!-- Accordion Item -->
<template #accordion>
  <div
    name="accordionItem"
    ref="accordionItem"
    :class="['border-b', customClass]"
    v-bind="attrs"
  >
    <slot></slot>
  </div>
</template>