<script lang="ts" setup>
useHead({
  titleTemplate: (title) => {
    return title ? `${title} - Telekomunikasi` : 'Telekomunikasi'
  },
})
</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
