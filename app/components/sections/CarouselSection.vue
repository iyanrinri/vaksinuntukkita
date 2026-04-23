<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const props = defineProps({
  slides: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["navigate"]);
const currentSlide = ref(0);
let intervalId;

const startAutoplay = () => {
  if (intervalId) clearInterval(intervalId);
  intervalId = setInterval(() => {
    currentSlide.value = (currentSlide.value + 1) % props.slides.length;
  }, 5000);
};

const stopAutoplay = () => {
  if (intervalId) {
    clearInterval(intervalId);
    intervalId = null;
  }
};

const setSlide = (index) => {
  currentSlide.value = index;
  startAutoplay();
};

onMounted(startAutoplay);
onUnmounted(stopAutoplay);
</script>

<template>
  <section class="section-carousel">
    <div class="carousel" @mouseenter="stopAutoplay" @mouseleave="startAutoplay">
      <div
        class="carousel-inner"
        :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
      >
        <div
          v-for="(slide, index) in slides"
          :key="index"
          class="carousel-item"
        >
          <img class="carousel-image" :src="slide.image" :alt="slide.title" />
          <div class="carousel-overlay"></div>
          <div class="carousel-caption" :class="{ active: currentSlide === index }">
            <p class="carousel-kicker">#VaksinUntukKita</p>
            <h1>{{ slide.title }}</h1>
            <p>{{ slide.description }}</p>
            <button class="carousel-cta" @click="emit('navigate', slide.targetId)">
              {{ slide.ctaLabel }}
            </button>
          </div>
        </div>
      </div>

      <div class="carousel-indicators">
        <span
          v-for="(_, index) in slides"
          :key="index"
          :class="{ active: currentSlide === index }"
          @click="setSlide(index)"
        ></span>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section-carousel {
  position: relative;
  overflow: hidden;
  height: calc(100vh - 80px);
  background-color: #f0f0f0;
}

.carousel {
  position: relative;
  width: 100%;
  height: 100%;
}

.carousel-inner {
  display: flex;
  height: 100%;
  transition: transform 0.5s ease-in-out;
}

.carousel-item {
  min-width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
}

.carousel-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}

.carousel-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, rgba(0, 0, 0, 0.62) 0%, rgba(0, 0, 0, 0.35) 45%, rgba(0, 0, 0, 0.15) 100%);
}

.carousel-caption {
  position: absolute;
  top: 50%;
  left: 8%;
  width: min(640px, 85%);
  transform: translateY(-50%);
  color: white;
  z-index: 2;
  opacity: 0;
  pointer-events: none;
}

.carousel-caption.active {
  opacity: 1;
  pointer-events: auto;
}

.carousel-caption.active .carousel-kicker,
.carousel-caption.active h1,
.carousel-caption.active p,
.carousel-caption.active .carousel-cta {
  animation: captionIn 0.6s ease forwards;
}

.carousel-caption.active h1 {
  animation-delay: 0.1s;
}

.carousel-caption.active p {
  animation-delay: 0.22s;
}

.carousel-caption.active .carousel-cta {
  animation-delay: 0.34s;
}

.carousel-kicker {
  font-size: 0.9rem;
  letter-spacing: 0.08em;
  font-weight: 700;
  margin-bottom: 0.8rem;
  color: #ffd9db;
  opacity: 0;
}

.carousel-caption h1 {
  font-size: clamp(1.8rem, 4vw, 3.4rem);
  line-height: 1.1;
  margin: 0 0 1rem;
  text-shadow: 0 10px 30px rgba(0, 0, 0, 0.28);
  opacity: 0;
}

.carousel-caption p {
  font-size: clamp(1rem, 2vw, 1.25rem);
  max-width: 580px;
  line-height: 1.6;
  margin: 0 0 1.8rem;
  color: rgba(255, 255, 255, 0.95);
  opacity: 0;
}

.carousel-cta {
  border: none;
  background-color: var(--primary-red);
  color: white;
  font-weight: 700;
  border-radius: 999px;
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease, background-color 0.25s ease;
  box-shadow: 0 10px 30px rgba(238, 28, 37, 0.3);
  opacity: 0;
}

.carousel-cta:hover {
  transform: translateY(-2px);
  background-color: #d91620;
  box-shadow: 0 16px 28px rgba(238, 28, 37, 0.4);
}

.carousel-indicators {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
}

.carousel-indicators span {
  width: 12px;
  height: 12px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s;
}

.carousel-indicators span.active {
  background-color: var(--primary-red);
  border: 2px solid white;
}

@media (max-width: 768px) {
  .section-carousel {
    height: 70vh;
  }

  .carousel-caption {
    left: 1.2rem;
    width: calc(100% - 2.4rem);
  }

  .carousel-caption p {
    margin-bottom: 1.1rem;
  }

  .carousel-cta {
    width: 100%;
    max-width: 240px;
  }
}

@keyframes captionIn {
  from {
    opacity: 0;
    transform: translateY(18px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
