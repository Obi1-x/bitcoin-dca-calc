<template>
  <UiCard class="mt-8 dark:bg-gray-800">
    <UiCardHeader>
      <UiCardTitle class="text-2xl font-bold text-center">Frequently Asked Questions</UiCardTitle>
    </UiCardHeader>
    <UiCardContent>
      <UiAccordion type="single" collapsible class="w-full">
      <UiAccordionItem
        v-for="(faq, index) in faqs"
        :key="index"
        :value="`item-${index}`"
        class="rounded-lg"
      >
        <UiAccordionTrigger
          :index="index"
          :openIndex="openIndex"
          @toggle="toggle"
          class="text-left hover:text-[#4AE54A] dark:text-white"
        >
          {{ faq.question }}
        </UiAccordionTrigger>
        <UiAccordionContent
          :index="index"
          :openIndex="openIndex"
          class="text-gray-600 dark:text-gray-300"
        >
          {{ faq.answer }}
        </UiAccordionContent>
      </UiAccordionItem>
    </UiAccordion>
    </UiCardContent>
  </UiCard>
</template>

<script setup>
import { ref } from 'vue';

const faqs = ref([
  {
    question: "What is Dollar Cost Averaging (DCA)?",
    answer:
      "Dollar Cost Averaging is an investment strategy where you invest a fixed amount of money at regular intervals, regardless of the asset's price. This helps reduce the impact of volatility and eliminates the need to time the market.",
  },
  {
    question: "Why should I DCA into Bitcoin?",
    answer:
      "DCA-ing into Bitcoin helps mitigate the risks associated with Bitcoin's price volatility. Instead of trying to time the market perfectly, you build your position gradually over time, potentially reducing your average purchase price and emotional stress.",
  },
  {
    question: "How often should I make Bitcoin purchases?",
    answer:
      "The frequency of purchases depends on your investment goals and financial situation. Common intervals are daily, weekly, or monthly. More frequent purchases can help smooth out price volatility, but consider transaction fees when deciding your frequency.",
  },
  {
    question: "What amount should I invest?",
    answer:
      "You should only invest what you can afford to lose. A common recommendation is to invest a small percentage of your monthly income that won't affect your essential expenses. Start small and adjust based on your comfort level and financial situation.",
  },
  {
    question: "Where should I store my Bitcoin?",
    answer:
      "For small amounts, reputable exchanges can be convenient. However, as your Bitcoin holdings grow, consider moving them to a self-custodial wallet where you control the private keys. Hardware wallets are considered one of the most secure storage solutions.",
  },
  {
    question: "Is it too late to start investing in Bitcoin?",
    answer:
      "Bitcoin is still in its early adoption phase. While past performance doesn't guarantee future results, Bitcoin's fixed supply and growing institutional adoption suggest potential long-term value. DCA can be an effective way to start building your position regardless of current price.",
  },
]);

const openIndex = ref(null);

const toggle = (index) => {
  openIndex.value = openIndex.value === index ? null : index;
};

</script>
