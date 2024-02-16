<template>
    <div class="slider-container">
        <div class="slider-images">
            <img v-for="(image, index) in images" :key="index" :src="image" :class="{ active: index === state.activeImage }" />
        </div>
        <button class="arrow left-arrow" @click="prevImage">&#10094;</button>
        <button class="arrow right-arrow" @click="nextImage">&#10095;</button>
        <canvas ref="canvas"></canvas>
        <div class="menu">
            <a href="/bio">Bio</a>
        </div>
    </div>
</template>
  
<script setup lang="ts">
import { ref, onMounted, reactive } from 'vue';
import { LazyBrush } from 'lazy-brush';

const images = [
    'img/image-1.webp',
    'img/image-2.webp',
    'img/image-3.webp',
    'img/image-3.webp'
];
const state = reactive({
    activeImage: 0
});

const canvasRef = ref<HTMLCanvasElement | null>(null);
let lazy = null;

function nextImage() {
    state.activeImage = (state.activeImage + 1) % images.length;
}

function prevImage() {
    state.activeImage = (state.activeImage - 1 + images.length) % images.length;
}

onMounted(() => {
    const canvas = canvasRef.value;
    if (!canvas) return;

    const ctx = canvas.getContext('2d');
    if (!ctx) return;

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    lazy = new LazyBrush({
        radius: 30,
        enabled: true,
        initialPoint: { x: 0, y: 0 }
    });

    let isDrawing = false;

    canvas.addEventListener('mousedown', (e) => {
        isDrawing = true;
        lazy.update({ x: e.pageX, y: e.pageY }, { both: true });
    });

    canvas.addEventListener('mousemove', (e) => {
        if (!isDrawing) return;
        lazy.update({ x: e.pageX, y: e.pageY });
        const { x, y } = lazy.getBrushCoordinates();
        if (lazy.brushHasMoved()) {
            ctx.lineTo(x, y);
            ctx.stroke();
        }
    });

    canvas.addEventListener('mouseup', () => {
        isDrawing = false;
        ctx.closePath();
    });

    canvas.addEventListener('mouseleave', () => {
        isDrawing = false;
    });
});
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
}

.menu {
    position: absolute;
    top: 0;
    right: 0;
    padding: 20px;
    z-index: 15;
}

.menu a {
    color: #fff;
    text-decoration: none;
}
</style>