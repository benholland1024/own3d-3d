<script lang="ts" setup>
import { useLoader } from '@tresjs/core'
import { useGLTF } from '@tresjs/cientos'
const { scene, nodes, animations, materials } = await useGLTF('/logo.glb')



</script>

<template>
  <primitive :object="scene" :position="[-4,-2,0]"
    :scale="[10,10,10]"
    :rotation="[Math.PI/2,0,-Math.PI/4]"
  />
</template>
