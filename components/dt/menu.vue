<script lang="ts" setup>
import gsap from 'gsap'

const router = useRouter()

const model = defineModel<boolean>({
  default: false,
})

const refMenu = ref<HTMLElement>()

const clickMenu = function (to: string) {
  model.value = false
  router.push(to)
}

watch(model, (val) => {
  if (val) {
    nextTick(() => {
      gsap.to(refMenu.value!, {
        display: 'block',
        opacity: 1,
        duration: 0.5,
      })
    })
  }
  else {
    gsap.to(refMenu.value!, {
      display: 'none',
      opacity: 0,
      duration: 0.5,
    })
  }
})
</script>

<template>
  <div
    ref="refMenu"
    class="dt-menu"
  >
    <video autoplay muted loop class="dt-layout-background-video">
      <source src="~/assets/videos/background-2.mp4">
    </video>
    <button class="dt-menu-close" @click="model = false">
      <img src="~/assets/images/close-logo.svg">
    </button>
    <div class="dt-menu-content">
      <div class="dt-menu-content-left">
        <img src="~/assets/images/pln-logo.svg">
      </div>
      <div class="dt-menu-content-right">
        <div>
          <div class="dt-menu-item">
            <a class="dt-menu-link" @click="clickMenu('/')">
              Home
            </a>
          </div>
          <div class="dt-menu-item">
            <a class="dt-menu-link" @click="clickMenu('/about-us')">
              ABOUT US
            </a>
          </div>
          <div class="dt-menu-item">
            <a class="dt-menu-link" @click="clickMenu('/services')">
              OUR SERVICES
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
