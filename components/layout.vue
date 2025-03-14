<template>
  <div> <!-- Transform to NuxtLayout after fixing SSR bug, which causes hydration issues -->
    <header class="flex items-center justify-between mb-8 bg-white dark:bg-gray-800 p-4 rounded-lg">
      <div class="flex items-center space-x-4">
        <NuxtLink to="https://unbank.com">
          <img 
            src="https://hebbkx1anhila5yf.public.blob.vercel-storage.com/logo.2.BWifZoIN-cxMJgeWBW6UhFKzTU2ZpHIWGxEsByl.svg"
            alt="DCA Signals Logo"
            width="164"
            height="28"
          />
        </NuxtLink>
        <nav class="hidden sm:flex space-x-4">
          <NuxtLink to="/" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">
            DCA Calculator
          </NuxtLink>
          <NuxtLink to="/moonCalculator" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">
            MOON Calculator
          </NuxtLink>
          <NuxtLink to="/btcstimi" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">
            Stimulus Calculator
          </NuxtLink>
          <NuxtLink to="/affiliate/bitcoin-source" class="text-gray-600 hover:text-gray-900 dark:text-gray-300 dark:hover:text-white">
            Bitcoin Source
          </NuxtLink>
        </nav>
      </div>
    </header>
  </div>
</template>
