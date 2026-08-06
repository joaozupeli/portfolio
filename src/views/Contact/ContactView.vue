<script setup lang="ts">
import { onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  gsap.from('#contact .section-label', {
    scrollTrigger: {
      trigger: '#contact',
      start: 'top 80%',
      toggleActions: 'play none none reverse',
    },
    y: 20,
    opacity: 0,
    duration: 0.6,
    ease: 'power4.out',
  })

  gsap.from('#contact .page-title', {
    scrollTrigger: {
      trigger: '#contact',
      start: 'top 75%',
      toggleActions: 'play none none reverse',
    },
    y: 80,
    opacity: 0,
    duration: 1,
    ease: 'power4.out',
  })

  gsap.from('#contact .contact-text', {
    scrollTrigger: {
      trigger: '#contact .contact-text',
      start: 'top 85%',
      toggleActions: 'play none none reverse',
    },
    y: 40,
    opacity: 0,
    duration: 0.8,
    ease: 'power4.out',
  })

  gsap.from('#contact .contact-link', {
    scrollTrigger: {
      trigger: '#contact .contact-links',
      start: 'top 85%',
      toggleActions: 'play none none reverse',
    },
    x: -30,
    opacity: 0,
    duration: 0.6,
    stagger: 0.1,
    ease: 'power4.out',
  })
})
</script>

<template>
  <section id="contact" class="contact-section">
    <span class="section-label">04 / Contato</span>
    <h2 class="page-title">Vamos conversar</h2>
    <p class="contact-text">
      Tem um project em mente ou um engineering challenge? Vamos build algo incrível juntos.
    </p>
    <div class="contact-links">
      <a href="mailto:seu@email.com" class="contact-link">
        <span class="link-label">Email</span>
        <span class="link-value">seu@email.com</span>
      </a>
      <a href="https://github.com/joaozupeli" target="_blank" class="contact-link">
        <span class="link-label">GitHub</span>
        <span class="link-value">github.com/joaozupeli</span>
      </a>
      <a href="https://www.linkedin.com/in/joão-zupeli-612a17287/" target="_blank" class="contact-link">
        <span class="link-label">LinkedIn</span>
        <span class="link-value">linkedin.com/in/joão-zupeli-612a17287</span>
      </a>
    </div>
    <footer class="footer">
      <span class="footer-text">&copy; 2026 zpFolio — Designed & Built with Vue.js + GSAP</span>
    </footer>
  </section>
</template>

<style scoped>
.contact-section {
  min-height: 100vh;
  padding: 8rem 3rem 3rem;
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
  margin: 0 0 2rem;
}

.contact-text {
  font-size: clamp(1.1rem, 1.8vw, 1.4rem);
  color: rgba(255, 255, 255, 0.5);
  font-weight: 300;
  margin: 0 0 4rem;
  max-width: 500px;
  line-height: 1.6;
}

.contact-links {
  display: flex;
  flex-direction: column;
}

.contact-link {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem 0;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  text-decoration: none;
  transition: opacity 0.3s ease;
}

.contact-link:last-child {
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.contact-link:hover {
  opacity: 0.6;
}

.link-label {
  font-size: 0.85rem;
  color: rgba(255, 255, 255, 0.4);
  text-transform: uppercase;
  letter-spacing: 0.15em;
  font-weight: 400;
}

.link-value {
  font-size: 1.1rem;
  color: #fff;
  font-weight: 300;
}

.footer {
  margin-top: auto;
  padding-top: 4rem;
}

.footer-text {
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.2);
  font-weight: 300;
}

@media (max-width: 768px) {
  .contact-link {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
}
</style>
