<script lang="ts" setup>
import { useLoop } from '@tresjs/core'
import { ref } from 'vue'
import { shallowRef } from 'vue'



// const particles = ref([])             //  Stores our particles
// for (let i = 0; i < 2; i++) {
//   for (let j = 0; j < 2; j++) {
//     const particleRef = shallowRef()
//     particleRef.position = { x: i, y: -1, z: j};
//     particles.value.push(particleRef);
//     particles.value[particles.length-1].value.position = { x: i, y: -1, z: j};
//   }
// }
const particle = shallowRef()
const particle1 = shallowRef()
const particle2 = shallowRef()
const particle3 = shallowRef()
const particle4 = shallowRef()
const particle5 = shallowRef()

const { onBeforeRender } = useLoop()

let max = 4;
let min = 2;


onBeforeRender(({ delta, elapsed }) => {
  delta = delta * 4
  // I will run at every frame ~ 60FPS (depending of your monitor)
  if (particle.value && particle.value.position.y > 3) {
    particle.value.position.y = -2;
    particle.value.position.x = Math.floor(Math.random() * max) - min;
    particle.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle.value) { 
    particle.value.position.x += delta * 0.4
    particle.value.position.y += delta + 0.03;
  }

  if (particle1.value && particle1.value.position.y > 3) {
    particle1.value.position.y = -2;
    particle1.value.position.x = Math.floor(Math.random() * max) - min;
    particle1.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle1.value) { 
    particle1.value.position.x += delta * 0.2
    particle1.value.position.y += delta 
  }

  if (particle2.value && particle2.value.position.y > 3) {
    particle2.value.position.y = -2;
    particle2.value.position.x = Math.floor(Math.random() * max) - min;
    particle2.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle2.value) { 
    particle2.value.position.x += delta * 0.3
    particle2.value.position.y += delta 
  }

  if (particle3.value && particle3.value.position.y > 3) {
    particle3.value.position.y = -2;
    particle3.value.position.x = Math.floor(Math.random() * max) - min;
    particle3.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle3.value) { 
    particle3.value.position.x += delta * 0.2
    particle3.value.position.y += delta + 0.01
  }

  if (particle4.value && particle4.value.position.y > 3) {
    particle4.value.position.y = -2;
    particle4.value.position.x = Math.floor(Math.random() * max) - min;
    particle4.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle4.value) { 
    particle4.value.position.x += delta * 0.2
    particle4.value.position.y += delta + 0.005;
  }

  if (particle5.value && particle5.value.position.y > 3) {
    particle5.value.position.y = -2;
    particle5.value.position.x = Math.floor(Math.random() * max) - min;
    particle5.value.position.z = Math.floor(Math.random() * max) - min;
  } else if (particle5.value) { 
    particle5.value.position.x += delta * 0.2
    particle5.value.position.y += delta 
  }

})

const scale = ref([0.02,0.02,0.02])

</script>

<template>
  <!--  Particles  -->
  <!-- <TresMesh v-for="(particle, i) in particles" :key="'particle-' + i"
    :scale="[0.1,0.1,0.1]" :ref="particle"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh> -->
  <TresMesh 
    :scale="scale" ref="particle"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
  <TresMesh 
    :scale="scale" ref="particle1"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
  <TresMesh 
    :scale="scale" ref="particle2"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
  <TresMesh 
    :scale="scale" ref="particle3" :position="[0,10,0]"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
  <TresMesh 
    :scale="scale" ref="particle4" :position="[3,2,0]"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
  <TresMesh 
    :scale="scale" ref="particle5" :position="[-1,-4,2]"
  >
    <TresSphereGeometry  />
    <TresMeshStandardMaterial color="#FF9602" emissive="#FF9602" emissiveIntensity="1"/>
  </TresMesh>
</template>
