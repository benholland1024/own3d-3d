<script lang="ts" setup>
import { TresCanvas } from '@tresjs/core'
import { extend } from '@tresjs/core'
import { OrbitControls, useGLTF } from '@tresjs/cientos'
import { ref } from 'vue'

import logo from './components/landing/logo.vue'
import room from './components/landing/room.vue'


extend({ OrbitControls })

const intensity = ref(5);
const rot = ref(1);
</script>

<template>
  <div id="controls">
    <p>Intensity:
      <input type="number" v-model="intensity"/>
      <input type="range" v-model="intensity"/>
    </p>
    <p>Rotation:
      <input type="number" v-model="rot" step="0.01" max="4" min="0"/>
      <input type="range" v-model="rot" step="0.01" max="4" min="0"/>
    </p>
    <p>{{ intensity }}</p>
  </div>
  <TresCanvas window-size clear-color="#555" shadows
    alpha>
    <TresPerspectiveCamera
      :position="[3, 3, 3]"
      :look-at="[0, 0, 0]"
    />
    <!--  Torus-->
    <!-- <TresMesh :position="[0, 0, 0]" :rotation="[0, rot, 0]" cast-shadow>
      <TresTorusGeometry :args="[1, 0.5, 16, 32]" />
      <TresMeshToonMaterial color="orange" />
    </TresMesh> -->

    <!--  Logo  -->
    <Suspense>
      <logo/>
    </Suspense>

    <!--  The room  -->
    <room></room>

    <!--  Box  -->
    <!-- <TresMesh :position="[0, 0, 0]" :scale="[3,3,3]" cast-shadow>
      <TresBoxGeometry :args="[1.5, 1.5, 1.5]" />
      <TresMeshToonMaterial color="#4F4F4F" />
    </TresMesh> -->
    
    <TresAmbientLight :intensity="1" />
    
    <TresPointLight :intensity="intensity" :position="[1, 1, 1]" cast-shadow/>
     <OrbitControls />
  </TresCanvas>
</template>

<style scoped>
#controls {
  position: absolute;
  z-index: 2;
  top: 5px;
  left: 5px;
  padding: 10px;
  background: rgba(0,0,0,0.5);
}
</style>
