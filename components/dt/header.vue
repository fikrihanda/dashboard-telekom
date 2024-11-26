<script lang="ts" setup>
import gsap from 'gsap'

const emits = defineEmits<{
  (e: 'toggle'): void
}>()

const refHeader = ref<HTMLElement>()

onMounted(() => {
  gsap.to(refHeader.value!, {
    keyframes: {
      '0%': {
        y: -100,
      },
      '100%': {
        y: 0,
      },
    },
    delay: 1.2,
    duration: 1,
  })
})
</script>

<template>
  <div ref="refHeader" class="dt-header">
    <img src="~/assets/images/header-logo.svg" class="dt-header-logo">
    <button class="dt-header-btn-menu" @click="emits('toggle')">
      <img src="~/assets/images/bars-logo.svg">
    </button>
  </div>
</template>
