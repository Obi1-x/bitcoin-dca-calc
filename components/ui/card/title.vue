<!-- Card Title -->
<template #title>
  <div
    name="cardTitle"
    ref="cardTitle"
    :class="['tracking-tight', customClass]"
    v-bind="attrs"
  >
    <slot></slot>
  </div>
</template>