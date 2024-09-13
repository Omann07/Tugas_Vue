<script setup>
import { ref } from 'vue'

const count = ref(0)
const boxColor = ref('grey');
const currentImageIndex = ref(0);

function changeColor() {
  const colors = ['red', 'green', 'blue', 'yellow'];
  boxColor.value = colors[Math.floor(Math.random() * colors.length)];
}

function nextImage() {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length;
}

function prevImage() {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length;
}
const images = [
  'https://via.placeholder.com/400x200?text=Image+1',
  'https://via.placeholder.com/400x200?text=Image+2',
  'https://via.placeholder.com/400x200?text=Image+3'
];  
</script>

<template>
  <p style="text-align: center;">{{ count }}</p>
  <button @click="count++">Count</button>

    <button @click="changeColor" >Ubah Warna Box</button>
    <div :style="{ backgroundColor: boxColor, height: '200px' }"></div>

    <div class="carousel">
      <button @click="prevImage" >Previous</button>
      <img :src="images[currentImageIndex]" alt="carousel image" style="height: 200px; width: 400px;" />
      <button @click="nextImage" style="display: inline;">Next</button>
    </div>

</template>
<style scoped>

button {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  cursor: pointer;
}

div > div {
  transition: background-color 0.3s ease;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carousel img {
  width: 400px;
  height: 200px;
  object-fit: cover;
  margin: 0 10px;
}
</style>