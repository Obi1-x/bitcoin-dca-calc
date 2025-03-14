<!-- Card Content -->
<template #content>
  <div
    name="cardContent"
    ref="cardContent"
    :class="['p-6 pt-0', customClass]"
    v-bind="attrs"
  >
    <slot></slot>
  </div>
</template>