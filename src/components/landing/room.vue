<script lang="ts" setup>

</script>

<template>
  <!--  The floor  -->
  <TresMesh :position="[0,-2,0]" 
    :rotation="[-Math.PI/2,0,0]" 
    :scale="[10,10,1]"
    cast-shadow
  >
    <TresPlaneGeometry :args="[1,1,16,32]" />
    <TresMeshToonMaterial color="#333" />
  </TresMesh>
  <!--  The left wall  -->
  <TresMesh :position="[-5,0,0]" 
    :rotation="[0,Math.PI/2,0]" 
    :scale="[10,10,1]"
    cast-shadow
  >
    <TresPlaneGeometry :args="[1,1,16,32]" />
    <TresMeshToonMaterial color="#444" />
  </TresMesh>
  <!--  The right wall  -->
  <TresMesh :position="[0,0,-5]" 
    :rotation="[0,0,0]" 
    :scale="[10,10,1]"
    cast-shadow
  >
    <TresPlaneGeometry :args="[1,1,16,32]" />
    <TresMeshToonMaterial color="#555" />
  </TresMesh>
</template>