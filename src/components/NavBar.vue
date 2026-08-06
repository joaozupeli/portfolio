<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const nav = ref<HTMLElement | null>(null)
const activeSection = ref('home')

const sections = ['home', 'work', 'about', 'contact']

function scrollTo(id: string) {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  gsap.from(nav.value, {
    y: -40,
    opacity: 0,
    duration: 1,
    ease: 'power3.out',
    delay: 0.5,
  })

  sections.forEach((id) => {
    ScrollTrigger.create({
      trigger: `#${id}`,
      start: 'top center',
      end: 'bottom center',
      onEnter: () => (activeSection.value = id),
      onEnterBack: () => (activeSection.value = id),
    })
  })
})
</script>

<template>
  <nav ref="nav" class="navbar">
    <a class="nav-logo" @click.prevent="scrollTo('home')">João Zupeli</a>
    <div class="nav-links">
      <a
        v-for="section in ['work', 'about', 'contact']"
        :key="section"
        :class="{ active: activeSection === section }"
        @click.prevent="scrollTo(section)"
      >
        {{ section === 'work' ? 'Trabalhos' : section === 'about' ? 'Sobre' : 'Contato' }}
      </a>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  align-items: center;
  padding: 1.5rem 3rem;
  z-index: 100;
  background: linear-gradient(to bottom, rgba(10, 10, 10, 0.9) 0%, rgba(10, 10, 10, 0) 100%);
}

.nav-logo {
  font-size: 1.4rem;
  font-weight: 700;
  color: #fff;
  text-decoration: none;
  letter-spacing: -0.02em;
  cursor: pointer;
  flex-shrink: 0;
}

.nav-links {
  display: flex;
  gap: 0.5rem;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(255, 255, 255, 0.06);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 100px;
  padding: 0.35rem;
}

.nav-links a {
  color: rgba(255, 255, 255, 0.5);
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 400;
  letter-spacing: 0.02em;
  transition: all 0.3s ease;
  cursor: pointer;
  padding: 0.45rem 1.2rem;
  border-radius: 100px;
}

.nav-links a:hover {
  color: #fff;
  background: rgba(255, 255, 255, 0.06);
}

.nav-links a.active {
  color: #fff;
  background: rgba(100, 108, 255, 0.15);
  border: 1px solid rgba(100, 108, 255, 0.25);
}
</style>
