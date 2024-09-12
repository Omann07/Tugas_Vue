<script setup>
import { ref } from 'vue'

const count = ref(0)
const boxColor = ref('grey');
function changeColor() {
  const colors = ['red', 'green', 'blue', 'yellow'];
  boxColor.value = colors[Math.floor(Math.random() * colors.length)];
}
</script>

<template>
  {{ count }}
  <button @click="count++">Count</button>

  
    <button @click="changeColor" >Ubah Warna Box</button>
    <div :style="{ backgroundColor: boxColor, width: '150px', height: '150px' }"></div>
</template>