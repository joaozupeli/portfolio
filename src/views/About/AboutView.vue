<script setup lang="ts">
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const pillars = [
  {
    title: 'Core Engineering',
    items: [
      { label: 'Architecture', value: 'Microservices, Event-Driven Design, SOLID Principles' },
      { label: 'Languages', value: 'TypeScript / JavaScript, Java' },
      { label: 'APIs', value: 'Designing e documentando APIs RESTful seguras' },
    ],
  },
  {
    title: 'Cloud & Infrastructure',
    items: [
      { label: 'Platforms', value: 'Oracle Cloud, Google Cloud (GCP), AWS' },
      { label: 'DevOps', value: 'Docker, CI/CD Pipelines' },
      { label: 'Version Control', value: 'Git, Git Flow' },
    ],
  },
  {
    title: 'Data Management',
    items: [
      { label: 'Databases', value: 'SQL Server, MySQL, MariaDB' },
    ],
  },
  {
    title: 'Frontend Synergy',
    items: [
      { label: 'Frameworks', value: 'Vue.js, Nuxt.js, React.js' },
    ],
  },
]

onMounted(() => {
  gsap.from('#about .section-label', {
    scrollTrigger: {
      trigger: '#about',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    y: 20,
    opacity: 0,
    duration: 0.6,
    ease: 'power4.out',
  })

  gsap.from('#about .page-title', {
    scrollTrigger: {
      trigger: '#about',
      start: 'top 75%',
      toggleActions: 'play none none reverse',
    },
    y: 80,
    opacity: 0,
    duration: 1,
    ease: 'power4.out',
  })

  gsap.from('#about .pillar', {
    scrollTrigger: {
      trigger: '#about .skills-grid',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    y: 60,
    opacity: 0,
    duration: 0.8,
    stagger: 0.15,
    ease: 'power4.out',
  })
})
</script>

<template>
  <section id="about" class="about-section">
    <span class="section-label">02 / Habilidades</span>
    <h2 class="page-title">Stack Técnica</h2>
    <div class="skills-grid">
      <div v-for="pillar in pillars" :key="pillar.title" class="pillar">
        <h3 class="pillar-title">{{ pillar.title }}</h3>
        <div class="pillar-items">
          <div v-for="item in pillar.items" :key="item.label" class="pillar-item">
            <span class="item-label">{{ item.label }}</span>
            <span class="item-value">{{ item.value }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  min-height: 100vh;
  padding: 8rem 3rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.section-label {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.3);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  margin-bottom: 1.5rem;
  font-weight: 400;
}

.page-title {
  font-size: clamp(2.5rem, 6vw, 5rem);
  font-weight: 700;
  color: #fff;
  letter-spacing: -0.03em;
  margin: 0 0 4rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 3rem;
  max-width: 1000px;
}

.pillar {
  padding: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
  background: rgba(255, 255, 255, 0.02);
}

.pillar-title {
  font-size: 0.85rem;
  color: #646cff;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  font-weight: 500;
  margin: 0 0 1.5rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.pillar-items {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}

.pillar-item {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
}

.item-label {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.35);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  font-weight: 400;
}

.item-value {
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 300;
  line-height: 1.5;
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
}
</style>
