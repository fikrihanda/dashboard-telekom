<script lang="ts" setup>
import Background from '~/assets/videos/background.mp4'
import Background2 from '~/assets/videos/background-2.mp4'

const route = useRoute()

const refVideo = ref<HTMLVideoElement>()
const toggle = ref(false)

const realBackground = function () {
  refVideo.value!.src = route.path === '/' ? Background : Background2
}

watch(() => route.path, realBackground)

onMounted(() => {
  realBackground()
})
</script>

<template>
  <Teleport to="body">
    <DtMenu
      v-model="toggle"
    />
  </Teleport>
  <div class="dt-layout">
    <video ref="refVideo" autoplay muted loop class="dt-layout-background-video">
      <source :src="Background">
    </video>
    <div class="dt-layout-container">
      <DtHeader @toggle="toggle = true" />
      <slot />
    </div>
  </div>
</template>
