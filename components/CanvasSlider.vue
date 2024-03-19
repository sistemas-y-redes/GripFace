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
      <a :style="{ color: linkColor }" href="/bio">Bio</a>
    </div>
    <div class="social-links">
      <a :style="{ color: linkColor }" href="/dossier">DOSSIER</a>
      <a :style="{ color: linkColor }" href="mailto:david@example.com">CONTACTO</a>
      <a :style="{ color: linkColor }" href="https://instagram.com">INSTAGRAM</a>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, reactive } from 'vue';
import { LazyBrush } from 'lazy-brush'

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

const linkColor = ref('black');

const canvasRef = ref(null);

onMounted(() => {
  // Definir canvas
  const canvas = canvasRef.value;
  const ctx = canvas.getContext('2d');
  if (!canvas) return;

  // Dibujar la mancha de tinta
  const drawInkBlob = (color) => {
    ctx.save(); // Guardar el estado actual del contexto
    ctx.beginPath();

    // Comenzar desde un punto inicial, creando una base redondeada
    ctx.moveTo(75, 50);
    ctx.quadraticCurveTo(50, 60, 75, 70); // Curva inferior
    ctx.quadraticCurveTo(100, 60, 75, 50); // Curva superior, cerrando la forma básica

    // Agregar detalles para una apariencia más orgánica
    ctx.moveTo(75, 50);
    ctx.bezierCurveTo(55, 45, 55, 75, 75, 70); // Detalle izquierdo
    ctx.moveTo(75, 50);
    ctx.bezierCurveTo(95, 45, 95, 75, 75, 70); // Detalle derecho

    // Más detalles irregulares alrededor de la base central
    ctx.bezierCurveTo(70, 80, 80, 90, 75, 100); // Extensión inferior
    ctx.moveTo(75, 50);
    ctx.bezierCurveTo(65, 30, 85, 30, 75, 50); // Extensión superior

    ctx.closePath();
    ctx.fillStyle = color; // Usar el color pasado como parámetro
    ctx.fill();
    ctx.restore(); // Restaurar el estado después de dibujar la mancha de tinta
  };

  // Definir el pincel
  const lazy = new LazyBrush({ radius: 10, enabled: true });
  let isDrawing = false;
  let canDraw = false; // Estado para controlar si el puntero puede dibujar

  // Definir los efectos de dibujo
  const setEffects = () => {
    ctx.lineWidth = 5;
    ctx.lineJoin = 'round';
    ctx.lineCap = 'round';

  };

  // Efectos adicionales, se pueden añadir a la constante setEffects
  // const gradient = ctx.createLinearGradient(0, 0, canvas.width, 0);
  //   gradient.addColorStop(0, 'magenta');
  //   gradient.addColorStop(0.5, 'blue');
  //   gradient.addColorStop(1, 'red');
  //   ctx.strokeStyle = gradient;
  //   ctx.shadowBlur = 10;
  //   ctx.shadowColor = 'rgba(0, 0, 0, 0.5)';

  // Función para ajustar el tamaño del canvas
  const resizeCanvas = () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    drawInkBlob(canDraw ? 'black' : 'pink'); // Redibujar la mancha de tinta con el color actual
  };
  // Llamar a resizeCanvas inmediatamente para establecer el tamaño inicial
  resizeCanvas();
  // Agregar un detector de eventos para ajustar el canvas cuando se cambia el tamaño de la ventana
  window.addEventListener('resize', resizeCanvas);
  onUnmounted(() => {
    window.removeEventListener('resize', resizeCanvas);
  });

  const getCoordinates = (e) => {
    if (e.touches && e.touches.length > 0) {
      const rect = canvas.getBoundingClientRect();
      return { x: e.touches[0].clientX - rect.left, y: e.touches[0].clientY - rect.top };
    } else {
      return { x: e.offsetX, y: e.offsetY };
    }
  };

  const startDrawing = (e) => {
    e.preventDefault();
    if (!canDraw) return;
    isDrawing = true;
    setEffects();
    const coords = getCoordinates(e);
    lazy.update(coords);
    ctx.moveTo(coords.x, coords.y);
    ctx.beginPath();
  };

  const draw = (e) => {
    e.preventDefault();
    if (!isDrawing || !canDraw) return;
    const coords = getCoordinates(e);
    lazy.update(coords);
    if (lazy.brushHasMoved()) {
      ctx.lineTo(lazy.brush.x, lazy.brush.y);
      ctx.stroke();
    }
  };

  const stopDrawing = (e) => {
    e.preventDefault();
    if (isDrawing) {
      isDrawing = false;
      ctx.beginPath();
    }
  };


  let insideActivationZone = false;
  const togglePainting = (e) => {
    e.preventDefault(); // Prevenir el comportamiento predeterminado en dispositivos táctiles
    const isTouchEvent = e.touches && e.touches.length > 0;
    const offsetX = isTouchEvent ? e.touches[0].clientX - canvas.getBoundingClientRect().left : e.offsetX;
    const offsetY = isTouchEvent ? e.touches[0].clientY - canvas.getBoundingClientRect().top : e.offsetY;

    const radius = 50;
    const distance = Math.sqrt((offsetX - 75) ** 2 + (offsetY - 50) ** 2);

    if (distance <= radius) {
      if (!insideActivationZone) {
        insideActivationZone = true;
        canDraw = !canDraw;
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        drawInkBlob(canDraw ? 'black' : 'pink');
        linkColor.value = canDraw ? 'orange' : 'black';
      }
    } else {
      insideActivationZone = false;
    }
  };

  // Event listeners para escritorio
  canvas.addEventListener('mousedown', startDrawing);
  canvas.addEventListener('mousemove', draw);
  canvas.addEventListener('mouseup', stopDrawing);
  canvas.addEventListener('mouseleave', stopDrawing);
  canvas.addEventListener('mousemove', togglePainting);

  // Event listeners para dispositivos táctiles
  canvas.addEventListener('touchstart', startDrawing, { passive: false });
  canvas.addEventListener('touchmove', draw, { passive: false });
  canvas.addEventListener('touchend', stopDrawing);
  canvas.addEventListener('touchcancel', stopDrawing);
});

// Funciones para el slider de imágenes
const prevImage = () => {
  state.activeImage = (state.activeImage - 1 + images.length) % images.length; // Cambiar a la imagen anterior
};

const nextImage = () => {
  state.activeImage = (state.activeImage + 1) % images.length; // Cambiar a la siguiente imagen
};

</script>

<style scoped>
.slider-container {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  margin: -8px;
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
}

.menu {
  position: absolute;
  /* Posicionamiento absoluto para sacar el menú del flujo normal y colocarlo sobre otros elementos */
  top: 20px;
  right: 20px;
  z-index: 20;
  /* Asegurar que el menú tenga un z-index más alto que el canvas y las imágenes */
}

.menu a {
  text-decoration: none;
  font-size: 24px;
  transition: color 0.3s;
}

.social-links {
  position: absolute;
  bottom: 4em;
  /* Ajusta esta propiedad para determinar la distancia desde la parte inferior */
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  justify-content: center;
  width: 100%;
  z-index: 20;
  color: var(--linkColor);
  /* Asume que tienes una variable CSS para el color de los enlaces */
  text-shadow:
    -1px -1px 0 #ffe7f3,
    1px -1px 0 #ffe7f3,
    -1px 1px 0 #ffe7f3,
    1px 1px 0 #ffe7f3;
}

.social-links a {
  text-decoration: none;
  font-size: x-large;
  margin: 0 1em;
}

@media screen and (max-width: 768px) {
  .social-links a {
    font-size: small;
    bottom: 1em;
  }
}
</style>