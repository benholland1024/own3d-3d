<script lang="ts" setup>
import { useLoop } from '@tresjs/core'
import { ref } from 'vue'
import { shallowRef } from 'vue'


const light = shallowRef()
const light1 = shallowRef()
const light2 = shallowRef()



const { onBeforeRender } = useLoop()



onBeforeRender(({ delta, elapsed }) => {
  delta = delta * 4
  // I will run at every frame ~ 60FPS (depending of your monitor)
  if (light.value) {
    // light.value.intensity += delta * 100;
    light.value.intensity = 50 * Math.sin(elapsed * 2) + 75
    light1.value.intensity = 10 * Math.sin(elapsed * 5 + 2) + 30
    light2.value.intensity = 10 * Math.sin(elapsed * 7 + 1) + 30

  }
})

const scale = ref([0.02,0.02,0.02])
const props = defineProps(['color'])

</script>

<template>
  <TresPointLight :intensity="30" :position="[-2, -1.5, -2]" cast-shadow
    :color="`hsl(${29 + props.color}, 100%, 50%)`" ref="light"
  />
  <TresPointLight :intensity="10" :position="[-1, -2, -3]" cast-shadow
    :color="`hsl(${357 + props.color}, 100%, 50%)`" ref="light1"
  />
  <TresPointLight :intensity="10" :position="[-3, -2, -1]" cast-shadow
    :color="`hsl(${300 + props.color}, 100%, 50%)`" ref="light2"
  />
</template>
