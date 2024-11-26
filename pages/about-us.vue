<script setup lang="ts">
import type { NuxtLinkProps } from '#app'
import type { DefineComponent } from 'vue'
import gsap from 'gsap'

useHead({
  title: 'About Us',
})

const refTitle = ref<HTMLElement>()
const refSubtitle = ref<HTMLElement>()
const refText = ref<HTMLElement>()
const refImg = ref<HTMLImageElement>()
const refBtn = ref<InstanceType<DefineComponent<NuxtLinkProps>>>()

const mountAnimation = function () {
  gsap.to(refTitle.value!, {
    opacity: 1,
    x: 0,
    duration: 1,
    delay: 1,
  })
  gsap.to(refSubtitle.value!, {
    opacity: 1,
    x: 0,
    duration: 1,
    delay: 1.2,
  })
  gsap.to(refText.value!, {
    opacity: 1,
    x: 0,
    duration: 1,
    delay: 1.4,
  })
  gsap.to(refImg.value!, {
    opacity: 1,
    x: 0,
    duration: 1,
    delay: 1.2,
  })
  gsap.to(refBtn.value!.$el, {
    opacity: 1,
    y: 0,
    duration: 1,
    delay: 1.6,
  })
}

onMounted(() => {
  mountAnimation()
})
</script>

<template>
  <div class="about-us">
    <div class="about-us-left">
      <div class="about-us-left-content">
        <div ref="refTitle" class="about-us-left-title">
          ABOUT US
        </div>
        <div ref="refSubtitle" class="about-us-left-subtitle">
          PLN ICON PLUS is a leading telecommunications company that is revolutionizing the industry.
        </div>
        <div ref="refText" class="about-us-left-text">
          It is building a robust fiber optic network to connect cities and villages, bridging the digital divide. The company offers innovative solutions like cloud services and cybersecurity, empowering businesses to thrive in the digital age. By focusing on innovation, customer satisfaction, and social responsibility, PLN ICON PLUS is shaping a brighter, more connected future for Indonesia.
        </div>
        <div class="about-us-left-services">
          <NuxtLink ref="refBtn" class="btn" to="/services">
            OUR SERVICES
          </NuxtLink>
        </div>
      </div>
    </div>
    <div class="about-us-right">
      <img ref="refImg" src="~/assets/images/about-us.svg" class="about-us-right-img">
    </div>
  </div>
</template>
