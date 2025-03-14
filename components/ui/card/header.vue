<!-- Card Header -->
<template>
  <div
    name="cardHeader"
    ref="cardHeader"
    :class="['flex flex-col space-y-1.5 p-6', customClass]"
    v-bind="attrs"
  >
    <slot></slot>
  </div>
</template>
