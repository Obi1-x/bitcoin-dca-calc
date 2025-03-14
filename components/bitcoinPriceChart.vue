<template>
  <UiCard class="dark:bg-gray-800 dark:text-white">
    <UiCardHeader>
      <UiCardTitle class="text-2xl font-semibold leading-none tracking-tight">Bitcoin Price (Last 365 Days)</UiCardTitle>
    </UiCardHeader>
    <UiCardContent class="p-6 h-[300px] min-h-[200px]">
      <client-only>
        <VChart :option="chartOptions"
                 class="w-full h-full"
                 autoresize />
      </client-only>
    </UiCardContent>
  </UiCard>
</template>

<script setup>
import { ref, computed } from "vue";

const priceData = ref([
  { date: "2024-01-01", price: 25000 },
  { date: "2024-02-01", price: 32000 },
  { date: "2024-03-01", price: 39000 },
  { date: "2024-04-01", price: 47000 },
  { date: "2024-05-01", price: 50000 },
]);

const chartOptions = computed(() => ({
  tooltip: {
    trigger: "axis",
    formatter: (params) => {
      const data = params[0];
      return `Date: ${data.name}<br/>Price: $${data.value.toLocaleString()}`;
    },
  },
  xAxis: {
    type: "category",
    data: priceData.value.map((d) => d.date),
    axisLabel: {
      rotate: 45,
      fontSize: 10,
    },
  },
  yAxis: {
    type: "value",
    axisLabel: {
      formatter: (value) => `$${(value / 1000).toFixed(0)}k`,
      fontSize: 10,
    },
  },
  series: [
    {
      name: "Bitcoin Price",
      type: "line",
      data: priceData.value.map((d) => d.price),
      smooth: true,
      lineStyle: {
        width: 2,
      },
      itemStyle: {
        color: "#4AE54A",
      },
    },
  ],
  grid: {
    left: "10%",
    right: "10%",
    bottom: "15%",
    containLabel: true,
  },
}));

</script>
