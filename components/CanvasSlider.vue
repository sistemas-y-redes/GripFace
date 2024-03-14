<template>
  <div class="slider-container">
    <div class="slider-images">
      <img v-for="(image, index) in images" :key="index" :src="image"
        :class="{ active: index === state.activeImage }" />
    </div>
    <button class="arrow left-arrow" @click="prevImage">&#10094;</button>
    <button class="arrow right-arrow" @click="nextImage">&#10095;</button>
    <canvas ref="canvasRef"></canvas>
    <div class="menu">
      <a href="/bio">Bio</a>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, reactive } from 'vue';
import { LazyBrush } from 'lazy-brush';

const images = [
  '/img/_28A7654-Edit.webp',
  'img/_28A8075-HDR.webp',
  'img/_28A8083-HDR.webp',
  'img/_28A8404.webp',
  'img/_28A8413.webp',
  'img/7G1A0902.webp',
  'img/7G1A0909.webp',
  'img/casa2.webp',
  'img/DSC_0838-Edit.webp',
  '/img/GRIP-19.webp',
  '/img/gripfaceesculturaweb.webp',
  '/img/gripfacesite.webp',
  '/img/P1211787.webp',
  '/img/P1222067.webp',
  '/img/P1222156.webp',

];

const state = reactive({
  activeImage: 0
});

const canvasRef = ref(null);

onMounted(() => {
  // Definición del canvas sobre el que pinta el puntero
  const canvas = canvasRef.value;
  if (!canvas) return;
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  
  // Pintar los círculos de activación/desactivación del puntero
  const circleLeftX = 50;
  const circleLeftY = 50;
  const circleLeftRadius = 20;
  const circleRightX = canvas.width - 50;
  const circleRightY = 50;
  const circleRightRadius = 20;
  const drawCircles = () => {
    // Dibujar el círculo izquierdo
    ctx.beginPath();
    ctx.arc(circleLeftX, circleLeftY, circleLeftRadius, 0, Math.PI * 2);
    ctx.strokeStyle = 'black';
    ctx.lineWidth = 2;
    ctx.stroke();

    // Dibujar el círculo derecho
    ctx.beginPath();
    ctx.arc(circleRightX, circleRightY, circleRightRadius, 0, Math.PI * 2);
    ctx.strokeStyle = 'black';
    ctx.lineWidth = 2;
    ctx.stroke();
  };
  drawCircles();

  // Efectos
  ctx.lineWidth = 5;
  ctx.strokeStyle = 'red';
  ctx.shadowColor = 'rgba(0, 0, 0, 0.5)';
  ctx.shadowBlur = 10;
  const gradient = ctx.createLinearGradient(0, 0, canvas.width, canvas.height);
  gradient.addColorStop(0, 'red');
  gradient.addColorStop(0.5, 'green');
  gradient.addColorStop(1, 'blue');
  ctx.strokeStyle = gradient;
  ctx.filter = 'blur(2px)';


  // Implementación de lazy-brush
  const lazy = new LazyBrush({ radius: 10, enabled: true });
  let isDrawing = false;
  const startDrawing = (e) => {
    isDrawing = true;
    lazy.update({ x: e.clientX, y: e.clientY }, { both: true });
    ctx.moveTo(lazy.brush.x, lazy.brush.y);
  };
  const draw = (e) => {
    if (!isDrawing) return;
    lazy.update({ x: e.clientX, y: e.clientY });
    if (lazy.brushHasMoved()) {
      ctx.lineTo(lazy.brush.x, lazy.brush.y);
      ctx.stroke();
    }
  };
  const stopDrawing = () => {
    isDrawing = false;
    ctx.beginPath();
  };
  canvas.addEventListener('mouseenter', startDrawing);
  canvas.addEventListener('mousemove', draw);
  canvas.addEventListener('mouseleave', stopDrawing);

});

// Funciones para el slider de imágenes
const prevImage = () => {
  state.activeImage = (state.activeImage - 1 + images.length) % images.length;
  console.log('previa');
};
const nextImage = () => {
  state.activeImage = (state.activeImage + 1) % images.length;
  console.log('siguiente');
};
</script>

<style scoped>
.slider-container {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

.slider-images img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0;
  transition: opacity 0.5s;
  z-index: 1;
}

.slider-images img.active {
  opacity: 1;
}

.arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  cursor: pointer;
  padding: 10px;
  z-index: 10;
}

.left-arrow {
  left: 0;
}

.right-arrow {
  right: 0;
}

canvas {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  /* Canvas por encima de las imágenes */
}
</style>
