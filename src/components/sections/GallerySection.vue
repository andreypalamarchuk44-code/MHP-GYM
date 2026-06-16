<template>
  <section id="gallery" class="gallery">

    <div class="container">

      <span class="section-eyebrow">
        Галерея
      </span>

      <h2 class="section-title">
        Атмосфера MHP GYM
      </h2>

      <p class="gallery__subtitle">
        Сучасний простір для тренувань,
        розвитку та досягнення нових цілей.
      </p>

      <div class="gallery__grid">

        <div
          v-for="(image,index) in images"
          :key="index"
          class="gallery__item"
          :class="`gallery__item--${index + 1}`"
          @click="openLightbox(index)"
        >
          <img
            :src="image"
            :alt="`MHP GYM ${index + 1}`"
            loading="lazy"
          >
        </div>

      </div>

    </div>

    <Teleport to="body">

      <Transition name="lightbox">

        <div
          v-if="selectedIndex !== null"
          class="lightbox"
          @click.self="closeLightbox"
        >

          <button
            class="lightbox__close"
            @click="closeLightbox"
          >
            ✕
          </button>

          <button
            class="lightbox__arrow lightbox__arrow--prev"
            @click.stop="prevImage"
          >
            ‹
          </button>

          <img
            :src="images[selectedIndex]"
            class="lightbox__image"
            alt=""
          >

          <button
            class="lightbox__arrow lightbox__arrow--next"
            @click.stop="nextImage"
          >
            ›
          </button>

          <div class="lightbox__counter">
            {{ selectedIndex + 1 }}
            /
            {{ images.length }}
          </div>

        </div>

      </Transition>

    </Teleport>

  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

import gym1 from '@/assets/images/gym1.jpg'
import gym2 from '@/assets/images/gym2.jpg'
import gym3 from '@/assets/images/gym3.jpg'
import gym4 from '@/assets/images/gym4.jpg'
import gym5 from '@/assets/images/gym5.jpg'
import gym6 from '@/assets/images/gym6.jpg'
import gym7 from '@/assets/images/gym7.jpg'
import gym8 from '@/assets/images/gym8.jpg'

const images = [
  gym1,
  gym2,
  gym3,
  gym4,
  gym5,
  gym6,
  gym7,
  gym8
]

const selectedIndex = ref(null)

const openLightbox = (index) => {
  selectedIndex.value = index
  document.body.style.overflow = 'hidden'
}

const closeLightbox = () => {
  selectedIndex.value = null
  document.body.style.overflow = ''
}

const nextImage = () => {
  selectedIndex.value =
    (selectedIndex.value + 1) % images.length
}

const prevImage = () => {
  selectedIndex.value =
    (selectedIndex.value - 1 + images.length) %
    images.length
}

const handleKeydown = (e) => {

  if (selectedIndex.value === null) return

  if (e.key === 'Escape') {
    closeLightbox()
  }

  if (e.key === 'ArrowRight') {
    nextImage()
  }

  if (e.key === 'ArrowLeft') {
    prevImage()
  }
}

onMounted(() => {
  window.addEventListener(
    'keydown',
    handleKeydown
  )
})

onUnmounted(() => {
  window.removeEventListener(
    'keydown',
    handleKeydown
  )
})
</script>

<style scoped>

.gallery {
  padding: 120px 0;
  background: var(--surface);
}

.gallery__subtitle {
  max-width: 700px;
  margin-top: 16px;
  color: var(--muted);
  line-height: 1.7;
}

.gallery__grid {
  margin-top: 60px;

  display: grid;

  grid-template-columns:
    repeat(4,1fr);

  grid-auto-rows: 260px;

  gap: 20px;
}

.gallery__item {
  position: relative;

  overflow: hidden;

  border-radius: 24px;

  cursor: pointer;
}

.gallery__item img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  transition:
    transform .6s ease,
    filter .4s ease;
}

.gallery__item:hover img {
  transform: scale(1.08);
  filter: brightness(1.08);
}

.gallery__item::after {
  content: '';

  position: absolute;
  inset: 0;

  background:
    linear-gradient(
      to top,
      rgba(0,0,0,.4),
      transparent
    );

  opacity: 0;

  transition: .3s;
}

.gallery__item:hover::after {
  opacity: 1;
}

/* Masonry */

.gallery__item--1 {
  grid-column: span 2;
  grid-row: span 2;
}

.gallery__item--4 {
  grid-row: span 2;
}

.gallery__item--6 {
  grid-column: span 2;
}

/* Lightbox */

:global(.lightbox) {
  position: fixed;
  inset: 0;

  z-index: 9999;

  background:
    rgba(0,0,0,.92);

  display: flex;

  align-items: center;
  justify-content: center;

  padding: 40px;
}

:global(.lightbox__image) {
  max-width: 90vw;
  max-height: 85vh;

  border-radius: 24px;

  box-shadow:
    0 30px 60px rgba(0,0,0,.5);
}

:global(.lightbox__close) {
  position: absolute;

  top: 25px;
  right: 30px;

  width: 50px;
  height: 50px;

  border: none;

  border-radius: 50%;

  cursor: pointer;

  font-size: 1.4rem;

  color: white;

  background:
    rgba(255,255,255,.12);
}

:global(.lightbox__arrow) {
  position: absolute;

  top: 50%;

  transform: translateY(-50%);

  width: 56px;
  height: 56px;

  border: none;

  border-radius: 50%;

  cursor: pointer;

  font-size: 2rem;

  color: white;

  background:
    rgba(255,255,255,.12);
}

:global(.lightbox__arrow--prev) {
  left: 30px;
}

:global(.lightbox__arrow--next) {
  right: 30px;
}

:global(.lightbox__counter) {
  position: absolute;

  bottom: 30px;

  color: white;

  font-size: 15px;

  font-weight: 600;
}

/* Animation */

.lightbox-enter-active,
.lightbox-leave-active {
  transition: .35s ease;
}

.lightbox-enter-from,
.lightbox-leave-to {
  opacity: 0;
}

/* Tablet */

@media (max-width: 992px) {

  .gallery__grid {
    grid-template-columns:
      repeat(2,1fr);
  }

  .gallery__item--1,
  .gallery__item--6 {
    grid-column: span 2;
  }
}

/* Mobile */

@media (max-width: 576px) {

  .gallery {
    padding: 90px 0;
  }

  .gallery__grid {
    grid-template-columns: 1fr;
    grid-auto-rows: 250px;
  }

  .gallery__item,
  .gallery__item--1,
  .gallery__item--4,
  .gallery__item--6 {
    grid-column: span 1;
    grid-row: span 1;
  }

  :global(.lightbox__arrow) {
    width: 46px;
    height: 46px;
  }

  :global(.lightbox__arrow--prev) {
    left: 10px;
  }

  :global(.lightbox__arrow--next) {
    right: 10px;
  }
}
</style>