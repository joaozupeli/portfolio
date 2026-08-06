<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'

const headline = ref<HTMLElement | null>(null)
const cursor = ref<HTMLElement | null>(null)
const summary = ref<HTMLElement | null>(null)
const socialLinks = ref<HTMLElement | null>(null)
const photoWrapper = ref<HTMLElement | null>(null)
const scrollIndicator = ref<HTMLElement | null>(null)
const roleTag = ref<HTMLElement | null>(null)

const headlineText = 'Construindo Sistemas Back-end Escaláveis com Precisão Arquitetural.'
const displayedText = ref('')

onMounted(() => {
  const tl = gsap.timeline({ defaults: { ease: 'power4.out' } })

  tl.from(roleTag.value, {
    y: 20,
    opacity: 0,
    duration: 0.8,
    delay: 0.3,
  })

  gsap.from(photoWrapper.value, {
    opacity: 0,
    scale: 1.05,
    duration: 1.4,
    delay: 0.4,
    ease: 'power3.out',
  })

  tl.then(() => {
    let i = 0
    const typeInterval = setInterval(() => {
      if (i < headlineText.length) {
        displayedText.value += headlineText[i]
        i++
      } else {
        clearInterval(typeInterval)
        gsap.to(cursor.value, {
          opacity: 0,
          repeat: -1,
          yoyo: true,
          duration: 0.5,
        })
        gsap.from(summary.value, {
          y: 40,
          opacity: 0,
          duration: 1,
          ease: 'power4.out',
        })
        gsap.from(socialLinks.value, {
          y: 20,
          opacity: 0,
          duration: 0.8,
          delay: 0.2,
          ease: 'power4.out',
        })
        gsap.from(scrollIndicator.value, {
          opacity: 0,
          duration: 1,
          delay: 0.3,
          ease: 'power4.out',
        })
      }
    }, 35)
  })

  gsap.to(scrollIndicator.value, {
    y: 10,
    repeat: -1,
    yoyo: true,
    duration: 1.2,
    ease: 'power1.inOut',
    delay: 3,
  })
})
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-layout">
      <div class="hero-content">
        <span ref="roleTag" class="role-tag">Software Engineer — Back-end Dev</span>
        <h1 ref="headline" class="hero-title">
          <span class="typed-text">{{ displayedText }}</span>
          <span ref="cursor" class="cursor">|</span>
        </h1>
        <div ref="summary" class="hero-summary">
          <p>
            Como Software Engineer especializado em Back-end Development,
            conecto a lógica de negócio complexa
            com infraestrutura de alta performance.
          </p>
          <p>
            Minha abordagem é fundamentada em
            <span class="highlight">SOLID principles</span> e
            <span class="highlight">Microservices architecture</span>,
            garantindo que toda API que construo não seja apenas funcional,
            mas resiliente e maintainable.
          </p>
          <p class="summary-secondary">
            Com uma base sólida em Node.js (TypeScript) e Java,
            projeto ecosystems RESTful que alimentam experiências digitais modernas.
          </p>
          <p class="summary-secondary">
            Desde containerization com Docker até deployment automatizado
            através de CI/CD pipelines.
          </p>
        </div>
        <div ref="socialLinks" class="social-links">
          <a href="https://github.com/joaozupeli" target="_blank" class="social-link">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"
              />
            </svg>
            <span>GitHub</span>
          </a>
          <a href="https://linkedin.com/in/seu-perfil" target="_blank" class="social-link">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
              <path
                d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
              />
            </svg>
            <span>LinkedIn</span>
          </a>
        </div>
      </div>
      <div ref="photoWrapper" class="hero-photo">
        <div class="photo-container">
          <img src="/assets/joao_zupeli.jpg" alt="João Zupeli" />
          <div class="photo-vignette"></div>
        </div>
      </div>
    </div>
    <div ref="scrollIndicator" class="scroll-indicator">
      <span class="scroll-text">rolar</span>
      <div class="scroll-line"></div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 3rem;
  position: relative;
}

.hero-layout {
  display: flex;
  align-items: center;
  gap: 3rem;
}

.hero-content {
  flex: 1;
  min-width: 0;
}

.hero-photo {
  flex-shrink: 0;
  width: 540px;
  height: 750px;
  position: relative;
  margin-left: -1rem;
}

.photo-container {
  width: 100%;
  height: 100%;
  position: relative;
  border-radius: 16px;
  overflow: hidden;
}

.photo-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

.photo-vignette {
  position: absolute;
  inset: 0;
  border-radius: 16px;
  box-shadow:
    inset 0 0 80px 40px #0a0a0a,
    inset 0 60px 60px -20px rgba(10, 10, 10, 0.6),
    inset 0 -60px 60px -20px rgba(10, 10, 10, 0.95);
  pointer-events: none;
}

.role-tag {
  display: inline-block;
  font-size: 0.8rem;
  color: #646cff;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  font-weight: 500;
  margin-bottom: 1.5rem;
  border: 1px solid rgba(100, 108, 255, 0.3);
  padding: 0.5rem 1rem;
  border-radius: 100px;
}

.hero-title {
  font-size: clamp(2.2rem, 5vw, 4.2rem);
  font-weight: 700;
  line-height: 1.15;
  letter-spacing: -0.03em;
  color: #fff;
  margin: 0;
  font-family: 'Inter', monospace;
}

.typed-text {
  display: inline;
}

.cursor {
  display: inline;
  color: #646cff;
  font-weight: 300;
  margin-left: 2px;
}

.hero-summary {
  margin-top: 2rem;
}

.hero-summary p {
  font-size: clamp(0.85rem, 1.1vw, 0.95rem);
  color: rgba(255, 255, 255, 0.55);
  line-height: 1.8;
  margin: 0 0 1rem;
  font-weight: 300;
}

.hero-summary .summary-secondary {
  color: rgba(255, 255, 255, 0.35);
}

.highlight {
  color: rgba(255, 255, 255, 0.85);
  font-weight: 400;
}

.social-links {
  display: flex;
  gap: 1.5rem;
  margin-top: 2rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: rgba(255, 255, 255, 0.45);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 400;
  transition: color 0.3s ease;
  padding: 0.5rem 0;
}

.social-link:hover {
  color: #646cff;
}

.social-link svg {
  flex-shrink: 0;
}

.scroll-indicator {
  position: absolute;
  bottom: 3rem;
  right: 3rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.scroll-text {
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.4);
  letter-spacing: 0.15em;
  text-transform: uppercase;
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: rgba(255, 255, 255, 0.2);
}

@media (max-width: 900px) {
  .hero-layout {
    flex-direction: column-reverse;
    gap: 2rem;
  }

  .hero-photo {
    width: 260px;
    height: 320px;
  }

  .hero-content {
    max-width: 100%;
  }
}
</style>
