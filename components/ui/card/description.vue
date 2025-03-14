<!-- Card Description -->
<template #description>
  <div
    name="cardDescription"
    ref="cardDescription"
    :class="['text-muted-foreground ', customClass]"
    v-bind="attrs"
  >
    <slot></slot>
  </div>
</template>