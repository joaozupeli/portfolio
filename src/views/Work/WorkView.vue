<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

interface Project {
  title: string
  description: string
  image: string
  tags: string[]
  github: string
  live: string
}

const projects: Project[] = [
  {
    title: 'Em breve',
    description: 'Primeiro projeto será adicionado aqui com detalhes completos.',
    image: '',
    tags: ['Microservices', 'Node.js', 'TypeScript'],
    github: '#',
    live: '#',
  },
  {
    title: 'Em breve',
    description: 'Segundo projeto será adicionado aqui com detalhes completos.',
    image: '',
    tags: ['Cloud', 'Docker', 'CI/CD'],
    github: '#',
    live: '#',
  },
  {
    title: 'Em breve',
    description: 'Terceiro projeto será adicionado aqui com detalhes completos.',
    image: '',
    tags: ['Full-stack', 'Vue.js', 'Java'],
    github: '#',
    live: '#',
  },
  {
    title: 'Em breve',
    description: 'Quarto projeto será adicionado aqui com detalhes completos.',
    image: '',
    tags: ['API', 'REST', 'PostgreSQL'],
    github: '#',
    live: '#',
  },
]

const svgContainer = ref<HTMLElement | null>(null)

onMounted(() => {
  gsap.from('#work .section-label', {
    scrollTrigger: {
      trigger: '#work',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    y: 20,
    opacity: 0,
    duration: 0.8,
    ease: 'power3.out',
  })

  gsap.from('#work .page-title', {
    scrollTrigger: {
      trigger: '#work',
      start: 'top 75%',
      toggleActions: 'play none none reverse',
    },
    y: 40,
    opacity: 0,
    duration: 1,
    ease: 'power3.out',
  })

  gsap.from('#work .project-card', {
    scrollTrigger: {
      trigger: '#work .carousel-viewport',
      start: 'top 85%',
      toggleActions: 'play none none reverse',
    },
    y: 50,
    opacity: 0,
    duration: 1,
    stagger: 0.15,
    ease: 'power3.out',
  })

  gsap.from('#work .scroll-hint', {
    scrollTrigger: {
      trigger: '#work .carousel-viewport',
      start: 'top 85%',
      toggleActions: 'play none none reverse',
    },
    opacity: 0,
    duration: 1,
    delay: 0.6,
    ease: 'power3.out',
  })

  const archTl = gsap.timeline({
    scrollTrigger: {
      trigger: '#work .architecture',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
  })

  archTl
    .from('#work .arch-title', {
      y: 30,
      opacity: 0,
      duration: 0.8,
      ease: 'power3.out',
    })
    .from(
      '#work .arch-node',
      {
        scale: 0,
        opacity: 0,
        duration: 0.6,
        stagger: 0.1,
        ease: 'back.out(1.7)',
      },
      '-=0.3',
    )
    .from(
      '#work .arch-line',
      {
        scaleX: 0,
        opacity: 0,
        duration: 0.5,
        stagger: 0.08,
        ease: 'power2.out',
        transformOrigin: 'left center',
      },
      '-=0.3',
    )
    .from(
      '#work .arch-line-v',
      {
        scaleY: 0,
        opacity: 0,
        duration: 0.5,
        stagger: 0.08,
        ease: 'power2.out',
        transformOrigin: 'top center',
      },
      '-=0.4',
    )
})
</script>

<template>
  <section id="work" class="work-section">
    <div class="work-header">
      <span class="section-label">01 / Trabalhos</span>
      <h2 class="page-title">Projetos</h2>
    </div>

    <div class="carousel-viewport">
      <div class="carousel-track">
        <div
          v-for="(project, index) in projects"
          :key="index"
          class="project-card"
        >
          <div class="card-image">
            <img
              v-if="project.image"
              :src="project.image"
              :alt="project.title"
            />
            <div v-else class="card-image-placeholder">
              <span class="placeholder-number">{{ String(index + 1).padStart(2, '0') }}</span>
            </div>
          </div>
          <div class="card-body">
            <h3 class="card-title">{{ project.title }}</h3>
            <p class="card-description">{{ project.description }}</p>
            <div class="card-tags">
              <span v-for="tag in project.tags" :key="tag" class="card-tag">{{ tag }}</span>
            </div>
            <div class="card-links">
              <a :href="project.github" target="_blank" class="card-link" aria-label="GitHub">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
                </svg>
                <span>GitHub</span>
              </a>
              <a :href="project.live" target="_blank" class="card-link" aria-label="Live">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M18 13v6a2 2 0 01-2 2H5a2 2 0 01-2-2V8a2 2 0 012-2h6"/>
                  <polyline points="15 3 21 3 21 9"/>
                  <line x1="10" y1="14" x2="21" y2="3"/>
                </svg>
                <span>Live</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-hint">
      <span>arraste ou role para ver mais</span>
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
        <line x1="5" y1="12" x2="19" y2="12"/>
        <polyline points="12 5 19 12 12 19"/>
      </svg>
    </div>

    <div ref="svgContainer" class="architecture">
      <h3 class="arch-title">Como estruturo um Microservice</h3>
      <div class="arch-diagram">
        <svg viewBox="0 0 700 320" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect class="arch-node" x="280" y="10" width="140" height="44" rx="8" stroke="#646cff" stroke-width="1.5" fill="rgba(100,108,255,0.08)" />
          <text x="350" y="37" text-anchor="middle" fill="#fff" font-size="13" font-family="Inter, sans-serif" font-weight="400">Client</text>

          <line class="arch-line-v" x1="350" y1="54" x2="350" y2="90" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" />

          <rect class="arch-node" x="260" y="90" width="180" height="44" rx="8" stroke="#646cff" stroke-width="1.5" fill="rgba(100,108,255,0.08)" />
          <text x="350" y="117" text-anchor="middle" fill="#646cff" font-size="13" font-family="Inter, sans-serif" font-weight="500">API Gateway</text>

          <line class="arch-line-v" x1="150" y1="134" x2="150" y2="180" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" />
          <line class="arch-line-v" x1="350" y1="134" x2="350" y2="180" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" />
          <line class="arch-line-v" x1="550" y1="134" x2="550" y2="180" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" />

          <line class="arch-line" x1="150" y1="134" x2="550" y2="134" stroke="rgba(255,255,255,0.12)" stroke-width="1.5" />

          <rect class="arch-node" x="70" y="180" width="160" height="44" rx="8" stroke="rgba(255,255,255,0.15)" stroke-width="1" fill="rgba(255,255,255,0.03)" />
          <text x="150" y="207" text-anchor="middle" fill="rgba(255,255,255,0.7)" font-size="12" font-family="Inter, sans-serif" font-weight="300">Auth Service</text>

          <rect class="arch-node" x="270" y="180" width="160" height="44" rx="8" stroke="rgba(255,255,255,0.15)" stroke-width="1" fill="rgba(255,255,255,0.03)" />
          <text x="350" y="207" text-anchor="middle" fill="rgba(255,255,255,0.7)" font-size="12" font-family="Inter, sans-serif" font-weight="300">Core Service</text>

          <rect class="arch-node" x="470" y="180" width="160" height="44" rx="8" stroke="rgba(255,255,255,0.15)" stroke-width="1" fill="rgba(255,255,255,0.03)" />
          <text x="550" y="207" text-anchor="middle" fill="rgba(255,255,255,0.7)" font-size="12" font-family="Inter, sans-serif" font-weight="300">Notification Svc</text>

          <line class="arch-line-v" x1="150" y1="224" x2="150" y2="264" stroke="rgba(255,255,255,0.08)" stroke-width="1" />
          <line class="arch-line-v" x1="350" y1="224" x2="350" y2="264" stroke="rgba(255,255,255,0.08)" stroke-width="1" />
          <line class="arch-line-v" x1="550" y1="224" x2="550" y2="264" stroke="rgba(255,255,255,0.08)" stroke-width="1" />

          <rect class="arch-node" x="90" y="264" width="120" height="36" rx="6" stroke="rgba(255,255,255,0.1)" stroke-width="1" fill="rgba(255,255,255,0.02)" />
          <text x="150" y="287" text-anchor="middle" fill="rgba(255,255,255,0.4)" font-size="11" font-family="Inter, sans-serif" font-weight="300">Auth DB</text>

          <rect class="arch-node" x="290" y="264" width="120" height="36" rx="6" stroke="rgba(255,255,255,0.1)" stroke-width="1" fill="rgba(255,255,255,0.02)" />
          <text x="350" y="287" text-anchor="middle" fill="rgba(255,255,255,0.4)" font-size="11" font-family="Inter, sans-serif" font-weight="300">Main DB</text>

          <rect class="arch-node" x="490" y="264" width="120" height="36" rx="6" stroke="rgba(255,255,255,0.1)" stroke-width="1" fill="rgba(255,255,255,0.02)" />
          <text x="550" y="287" text-anchor="middle" fill="rgba(255,255,255,0.4)" font-size="11" font-family="Inter, sans-serif" font-weight="300">Queue / MQ</text>
        </svg>
      </div>
    </div>
  </section>
</template>

<style scoped>
.work-section {
  min-height: 100vh;
  padding: 8rem 3rem 4rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow: hidden;
}

.work-header {
  margin-bottom: 3rem;
}

.section-label {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.3);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  margin-bottom: 1.5rem;
  font-weight: 400;
  display: block;
}

.page-title {
  font-size: clamp(2.5rem, 6vw, 5rem);
  font-weight: 700;
  color: #fff;
  letter-spacing: -0.03em;
  margin: 0;
}

.carousel-viewport {
  overflow-x: auto;
  overflow-y: hidden;
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
}

.carousel-viewport::-webkit-scrollbar {
  display: none;
}

.carousel-track {
  display: flex;
  gap: 1.5rem;
  padding-bottom: 0.5rem;
}

.project-card {
  flex-shrink: 0;
  width: 400px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.07);
  border-radius: 16px;
  overflow: hidden;
  transition: border-color 0.3s ease, transform 0.3s ease;
}

.project-card:hover {
  border-color: rgba(100, 108, 255, 0.3);
  transform: translateY(-4px);
}

.card-image {
  width: 100%;
  height: 220px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.02);
}

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease;
}

.project-card:hover .card-image img {
  transform: scale(1.05);
}

.card-image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, rgba(100, 108, 255, 0.06) 0%, rgba(100, 108, 255, 0.02) 100%);
}

.placeholder-number {
  font-size: 4rem;
  font-weight: 700;
  color: rgba(100, 108, 255, 0.15);
  letter-spacing: -0.03em;
}

.card-body {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.card-title {
  font-size: 1.3rem;
  font-weight: 600;
  color: #fff;
  margin: 0;
  letter-spacing: -0.02em;
}

.card-description {
  font-size: 0.88rem;
  color: rgba(255, 255, 255, 0.45);
  font-weight: 300;
  line-height: 1.6;
  margin: 0;
}

.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 0.25rem;
}

.card-tag {
  font-size: 0.72rem;
  color: #646cff;
  border: 1px solid rgba(100, 108, 255, 0.25);
  padding: 0.3rem 0.7rem;
  border-radius: 100px;
  letter-spacing: 0.05em;
  font-weight: 400;
}

.card-links {
  display: flex;
  justify-content: center;
  gap: 1.2rem;
  margin-top: 0.5rem;
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.06);
}

.card-link {
  display: flex;
  align-items: center;
  gap: 0.4rem;
  color: rgba(255, 255, 255, 0.4);
  text-decoration: none;
  font-size: 0.82rem;
  font-weight: 400;
  transition: color 0.3s ease;
  white-space: nowrap;
}

.card-link:hover {
  color: #646cff;
}

.card-link svg {
  flex-shrink: 0;
}

.scroll-hint {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-top: 2rem;
  color: rgba(255, 255, 255, 0.2);
  font-size: 0.75rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  font-weight: 300;
}

.scroll-hint svg {
  animation: hintArrow 1.5s ease-in-out infinite;
}

@keyframes hintArrow {
  0%, 100% { transform: translateX(0); }
  50% { transform: translateX(6px); }
}

.architecture {
  margin-top: 6rem;
}

.arch-title {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.4);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  font-weight: 400;
  margin: 0 0 2rem;
}

.arch-diagram {
  max-width: 700px;
}

.arch-diagram svg {
  width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  .project-card {
    width: 320px;
  }

  .card-image {
    height: 180px;
  }
}
</style>
