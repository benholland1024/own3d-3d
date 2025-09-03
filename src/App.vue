<script lang="ts" setup>
import { TresCanvas } from '@tresjs/core'
import { extend } from '@tresjs/core'

import { OrbitControls, useGLTF } from '@tresjs/cientos'
import { ref } from 'vue'

import logo from './components/landing/logo.vue'
import room from './components/landing/room.vue'
import particles from './components/landing/particles.vue'




extend({ OrbitControls })

//  Scene variables
const intensity = ref(5);             //  White light intensity
const camPos = ref([3,0,3]);          //  Camera position
const camLookAt = ref([0,-1,0]);      //  Point the camera is looking @




</script>

<template>

  <!---------------->
  <!--  Controls  -->
  <!---------------->
  <div id="controls" class="text-white text-xs [&_input]:mr-4">
    <p class="flex justify-between">Intensity:
      <span>
        <input type="number" v-model="intensity"/>
        <input type="range" v-model="intensity"/>
      </span>
    </p>
    <p v-for="(pos, i) in camPos" :key="i" class="flex justify-between">
      Cam position {{ i }}:
      <span>
        <input type="number" v-model="camPos[i]"/>
        <input type="range" v-model="camPos[i]"/>
      </span>
    </p>
    <p v-for="(pos, i) in camLookAt" :key="i" class="flex justify-between">
      Cam look at {{ i }}:
      <span>
        <input type="number" v-model="camLookAt[i]"/>
        <input type="range" v-model="camLookAt[i]"/>
      </span>
    </p>
  </div>

  <!-------------->
  <!--  Canvas  -->
  <!-------------->
  <TresCanvas window-size clear-color="#555" shadows
    alpha>
    <TresPerspectiveCamera
      :position="[camPos[0], camPos[1], camPos[2]]"
      :look-at="[camLookAt[0], camLookAt[1], camLookAt[2]]"
    />

    <!-- Axes  -->
    <TresAxesHelper/>

    <!--  Logo  -->
    <Suspense>
      <logo/>
    </Suspense>

    <!--  Particles  -->
    <particles/>

    <!--  The room  -->
    <room></room>

    <!--  Box  -->
    <!-- <TresMesh :position="[0, 0, 0]" :scale="[3,3,3]" cast-shadow>
      <TresBoxGeometry :args="[1.5, 1.5, 1.5]" />
      <TresMeshToonMaterial color="#4F4F4F" />
    </TresMesh> -->
    
    <TresAmbientLight :intensity="1" />
    
    <TresPointLight :intensity="intensity" :position="[1, 1, 1]" cast-shadow/>
    <TresPointLight :intensity="30" :position="[-2, -1.5, -2]" cast-shadow
      :color="'orange'"
    />
    <!-- <OrbitControls /> -->
  </TresCanvas>
</template>

<style scoped>
body {
  color: white;
}
#controls {
  position: absolute;
  z-index: 2;
  top: 5px;
  left: 5px;
  padding: 10px;
  background: rgba(0,0,0,0.5);
  width: 400px;
}
#controls input[type=number] {
  width: 50px;
}

</style>
