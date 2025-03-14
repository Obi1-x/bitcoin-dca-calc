<template>
  <div 
    name="card"
    ref="card"
    :class="['rounded-lg border bg-card text-card-foreground shadow-sm', customClass]"
    v-bind="attrs">
   <slot></slot>
  </div>
</template>