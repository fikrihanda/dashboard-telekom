<script lang="ts" setup>
import type { NuxtLinkProps } from '#app'
import type { DefineComponent } from 'vue'
import gsap from 'gsap'

useHead({
  title: 'PLN',
})

const refGlobe = ref<HTMLImageElement>()
const refTitle = ref<HTMLElement>()
const refBtn = ref<InstanceType<DefineComponent<NuxtLinkProps>>>()

const mountedAnimation = function () {
  gsap.to(refGlobe.value!, {
    keyframes: {
      '0%': {
        y: 100,
      },
      '50%': {
        y: -20,
      },
      '100%': {
        y: 0,
        opacity: 1,
      },
    },
    duration: 1.2,
  })
  gsap.to(refTitle.value!, {
    opacity: 1,
    duration: 1,
    delay: 1.4,
    y: 0,
  })
  gsap.to(refBtn.value!.$el, {
    opacity: 1,
    duration: 1,
    delay: 1.6,
    y: 0,
  })
}

const globeOnHover = function () {
  gsap.to(refGlobe.value!, {
    scale: 1.1,
  })
}
const gloneOnBlur = function () {
  gsap.to(refGlobe.value!, {
    scale: 1,
  })
}

onMounted(() => {
  mountedAnimation()
  refGlobe.value!.addEventListener('mouseenter', globeOnHover)
  refGlobe.value!.addEventListener('touchstart', globeOnHover)
  refGlobe.value!.addEventListener('mouseleave', gloneOnBlur)
  refGlobe.value!.addEventListener('touchend', gloneOnBlur)
})

onBeforeUnmount(() => {
  refGlobe.value!.removeEventListener('mouseenter', globeOnHover)
  refGlobe.value!.removeEventListener('touchstart', globeOnHover)
  refGlobe.value!.removeEventListener('mouseleave', gloneOnBlur)
  refGlobe.value!.removeEventListener('touchend', gloneOnBlur)
})
</script>

<template>
  <div class="home">
    <img ref="refGlobe" src="~/assets/images/globe.svg" class="home-globe">
    <div ref="refTitle" class="home-title">
      FUTURE <br>
      TELECOMMUNICATION
    </div>
    <NuxtLink ref="refBtn" to="/about-us" class="btn home-btn">
      START TO EXPLORE
    </NuxtLink>
  </div>
</template>
