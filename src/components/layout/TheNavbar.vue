<template>
  <header
    class="navbar"
    :class="{ scrolled }"
  >
    <div class="container navbar__inner">

      <a href="#hero" class="logo">
        <span>MHP</span> GYM
      </a>

      <nav class="desktop-nav">

        <a href="#programs">
          Напрямки
        </a>

        <a href="#trainers">
          Тренери
        </a>

        <a href="#membership">
          Абонементи
        </a>

        <a href="#contact">
          Контакти
        </a>

      </nav>

      <a
        href="#membership"
        class="cta"
      >
        Пробне тренування
      </a>

      <button
        class="burger"
        @click="toggleMenu"
      >
        <span />
        <span />
        <span />
      </button>

    </div>

    <Transition name="drawer">

      <div
        v-if="menuOpen"
        class="mobile-menu"
      >

        <a
          href="#programs"
          @click="closeMenu"
        >
          Напрямки
        </a>

        <a
          href="#trainers"
          @click="closeMenu"
        >
          Тренери
        </a>

        <a
          href="#membership"
          @click="closeMenu"
        >
          Абонементи
        </a>

        <a
          href="#contact"
          @click="closeMenu"
        >
          Контакти
        </a>

      </div>

    </Transition>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const menuOpen = ref(false)

const handleScroll = () => {
  scrolled.value = window.scrollY > 40
}

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value

  document.body.style.overflow =
    menuOpen.value
      ? 'hidden'
      : ''
}

const closeMenu = () => {
  menuOpen.value = false
  document.body.style.overflow = ''
}

onMounted(() => {
  window.addEventListener(
    'scroll',
    handleScroll
  )
})

onUnmounted(() => {
  window.removeEventListener(
    'scroll',
    handleScroll
  )
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;

  width: 100%;

  z-index: 1000;

  transition: .35s ease;
}

.navbar.scrolled {
  background:
    rgba(7,7,7,.92);

  backdrop-filter:
    blur(16px);

  border-bottom:
    1px solid rgba(255,255,255,.05);
}

.navbar__inner {
  height: 88px;

  display: flex;

  align-items: center;

  justify-content: space-between;
}

.logo {
  color: white;

  text-decoration: none;

  font-size: 1.6rem;

  font-weight: 900;
}

.logo span {
  color: var(--gold);
}

.desktop-nav {
  display: flex;
  gap: 36px;
}

.desktop-nav a {
  color: white;

  text-decoration: none;

  position: relative;
}

.desktop-nav a::after {
  content: '';

  position: absolute;

  bottom: -6px;
  left: 0;

  width: 0;
  height: 2px;

  background: var(--gold);

  transition: .3s;
}

.desktop-nav a:hover::after {
  width: 100%;
}

.cta {
  background: var(--gold);

  color: black;

  padding: 14px 22px;

  border-radius: 14px;

  text-decoration: none;

  font-weight: 700;
}

.burger {
  display: none;

  background: none;
  border: none;

  cursor: pointer;
}

.burger span {
  display: block;

  width: 28px;
  height: 3px;

  background: white;

  margin: 5px 0;

  border-radius: 10px;
}

.mobile-menu {
  position: fixed;

  top: 88px;
  left: 0;

  width: 100%;

  height: calc(100vh - 88px);

  background: #0d0d0d;

  display: flex;

  flex-direction: column;

  align-items: center;

  justify-content: center;

  gap: 30px;
}

.mobile-menu a {
  color: white;

  text-decoration: none;

  font-size: 1.3rem;
}

.drawer-enter-active,
.drawer-leave-active {
  transition: .3s;
}

.drawer-enter-from,
.drawer-leave-to {
  opacity: 0;
}

@media(max-width:900px){

  .desktop-nav,
  .cta {
    display: none;
  }

  .burger {
    display: block;
  }
}
</style>