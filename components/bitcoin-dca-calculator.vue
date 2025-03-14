<template>
  <UiCard class="bg-gradient-to-b from-[#4AE54A]/10 to-white dark:from-[#4AE54A]/5 dark:to-gray-800 dark:text-white"> 
    <UiCardHeader class="text-center">
      <UiCardTitle class="text-4xl font-bold">Dollar Cost Averaging Bitcoin</UiCardTitle>
      <UiCardDescription class="text-lg dark:text-gray-300">
        Calculate your Bitcoin profit with our DCA Calculator
      </UiCardDescription>
    </UiCardHeader>
    <UiCardContent>
      <div class="grid gap-6 md:grid-cols-2">
        <div class="space-y-4">
          
          <div class="space-y-2">
            <label for="frequency" class="text-sm leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70 dark:text-gray-300">Repeat Purchase:</label>
            <select name="frequency" 
                    id="frequency" 
                    class="flex h-10 w-full items-center justify-between rounded-md border ps-2 pe-6 dark:bg-gray-700 dark:text-white">
              <option value="daily" class="bg-hover-color-secondary">Daily</option>
              <option value="weekly">Weekly</option>
              <option value="monthly">Monthly</option>
            </select>
          </div>

          <div class="space-y-2">
            <label for="starting" class="text-sm leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70 dark:text-gray-300">Starting:</label>
            <select name="startingPeriod"
                    id="starting"
                    class="flex h-10 w-full items-center justify-between rounded-md border ps-2 pe-6 dark:bg-gray-700 dark:text-white">
              <option value="1">1 year ago</option>
              <option value="2">2 years ago</option>
              <option value="5">5 years ago</option>
              <option value="10">10 years ago</option>
            </select>
          </div>

          <div class="space-y-2">
            <label for="amount" class="text-sm leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70 dark:text-gray-300">Investment Amount ($):</label>
            <input id="amount" type="number" v-model="amount" class="flex h-10 w-full items-center justify-between rounded-md border ps-2 pe-6 dark:bg-gray-700 dark:text-white" />
          </div>

          <div class="space-y-2">
           <label htmlFor="compare" class="text-sm leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70 dark:text-gray-300">Compare with:</label>
           <select id="compare" class="flex h-10 w-full items-center justify-between rounded-md border ps-2 pe-6 dark:bg-gray-700 dark:text-white">
            <option value="none">None</option>
            <option value="sp500">S&P 500</option>
            <option value="gold">Gold</option>
           </select>
          </div>

          <button @click="calculateReturns"
                  class="inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 [&amp;_svg]:pointer-events-none [&amp;_svg]:size-4 [&amp;_svg]:shrink-0 h-10 px-4 py-2 w-full bg-[#4AE54A] text-black hover:bg-[#4AE54A]/90 dark:bg-[#4AE54A]/80 dark:text-white dark:hover:bg-[#4AE54A]">
            Calculate
          </button>
        </div>

        <div class="space-y-4 rounded-lg bg-white p-6 shadow-lg dark:bg-gray-800 dark:text-white">
          <div class="flex items-center justify-between border-b pb-2 dark:border-gray-700">
            <span class="font-medium">Invested Amount:</span>
            <span class="font-mono">${{ results.investedAmount.toLocaleString() }}</span>
          </div>
          <div class="flex items-center justify-between border-b pb-2 dark:border-gray-700">
            <span class="font-medium">Final Return:</span>
            <span class="font-mono">${{ results.finalReturn.toLocaleString() }}</span>
          </div>
          <div class="flex items-center justify-between border-b pb-2 dark:border-gray-700">
            <span class="font-medium">Difference:</span>
            <span class="font-mono text-[#4AE54A]">
              ${{String(results.finalReturn - results.investedAmount)}} (NaN%)
            </span>
          </div>
          <div class="flex items-center justify-between pt-2">
            <span class="font-medium">Bitcoin Accumulated:</span>
            <span class="flex items-center font-mono">
              <BitcoinLogo class="mr-2 h-4 w-4" />
              {{ results.bitcoinAccumulated.toFixed(8) }} BTC
            </span>
          </div>
        </div>
      </div>

      <div class="mt-8">
        <BitcoinPriceChart />
      </div>
      
      <FaqSection />

    </UiCardContent>
  </UiCard>
</template>

<script setup>
import { ref, watchEffect } from 'vue';

//import { Bitcoin } from 'lucide-vue-next';

const frequency = ref('daily');
const startingPeriod = ref('5');
const amount = ref('10');
const results = ref({
  investedAmount: 0,
  finalReturn: 0,
  difference: 0,
  percentageGain: 0,
  bitcoinAccumulated: 0,
});

const calculateReturns = () => {
  const investedAmount = Number(amount.value) * 365 * Number(startingPeriod.value);
  const estimatedReturn = investedAmount * 2.5;
  const bitcoinAccumulated = estimatedReturn / 40000;
  results.value = {
    investedAmount,
    finalReturn: estimatedReturn,
    bitcoinAccumulated,
  };
};

watchEffect(() => {
  calculateReturns();
});
</script>
