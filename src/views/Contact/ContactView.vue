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
      Tem um projeto em mente ou um desafio de engenharia? Vamos construir algo incrível juntos.
    </p>

    <div class="cta-buttons">
      <a href="/cv.pdf" target="_blank" rel="noopener noreferrer" class="cta-button cta-primary">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
          <polyline points="14 2 14 8 20 8"/>
          <line x1="12" y1="18" x2="12" y2="12"/>
          <line x1="9" y1="15" x2="15" y2="15"/>
        </svg>
        <span>Baixar Currículo</span>
      </a>
      <a
        href="https://wa.me/5569993921638?text=Ol%C3%A1%20Jo%C3%A3o!%20Vi%20seu%20portf%C3%B3lio%20e%20gostaria%20de%20conversar."
        target="_blank"
        rel="noopener noreferrer"
        class="cta-button cta-whatsapp"
      >
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
          <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
        </svg>
        <span>WhatsApp</span>
      </a>
    </div>

    <div class="contact-links">
      <a href="mailto:zupelidev@gmail.com" class="contact-link">
        <span class="link-label">Email</span>
        <span class="link-value">zupelidev@gmail.com</span>
      </a>
      <a href="https://github.com/joaozupeli" target="_blank" rel="noopener noreferrer" class="contact-link">
        <span class="link-label">GitHub</span>
        <span class="link-value">github.com/joaozupeli</span>
      </a>
      <a href="https://www.linkedin.com/in/jo%C3%A3o-zupeli-612a17287/" target="_blank" rel="noopener noreferrer" class="contact-link">
        <span class="link-label">LinkedIn</span>
        <span class="link-value">linkedin.com/in/joão-zupeli</span>
      </a>
    </div>
    <footer class="footer">
      <span class="footer-text">&copy; 2026 João Zupeli — Designed & Built with Vue.js + GSAP</span>
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
  margin: 0 0 2.5rem;
  max-width: 500px;
  line-height: 1.6;
}

.cta-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 3rem;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.9rem 1.5rem;
  border-radius: 100px;
  font-size: 0.95rem;
  font-weight: 500;
  text-decoration: none;
  transition: all 0.3s ease;
}

.cta-primary {
  background: #646cff;
  color: #fff;
  border: 1px solid #646cff;
}

.cta-primary:hover {
  background: #5558e3;
  border-color: #5558e3;
  transform: translateY(-2px);
}

.cta-whatsapp {
  background: rgba(37, 211, 102, 0.12);
  color: #25d366;
  border: 1px solid rgba(37, 211, 102, 0.3);
}

.cta-whatsapp:hover {
  background: rgba(37, 211, 102, 0.2);
  border-color: rgba(37, 211, 102, 0.5);
  transform: translateY(-2px);
}

.cta-button svg {
  flex-shrink: 0;
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
  .contact-section {
    padding: 8rem 1.5rem 3rem;
  }

  .contact-link {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }

  .cta-buttons {
    flex-direction: column;
  }

  .cta-button {
    justify-content: center;
    width: 100%;
  }
}
</style>
