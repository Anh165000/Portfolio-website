<template>
  <div class="portfolio-page">
    <!-- Fixed Navbar -->
    <Navbar />

    <!-- Main Content -->
    <main class="portfolio-main">
      <!-- Background Overlay -->
      <div class="background-decorations">
        <div class="gradient-orb gradient-orb-1"></div>
        <div class="gradient-orb gradient-orb-2"></div>
        <div class="gradient-orb gradient-orb-3"></div>
      </div>

      <!-- Bento Grid Container -->
      <div class="bento-grid">
        <!-- Hero Card - Span 2 columns x 2 rows -->
        <div class="bento-item hero-card" data-section="home">
          <HeroCard />
        </div>

        <!-- Tech Stack -->
        <div class="bento-item tech-stack" data-section="tech">
          <TechStack />
        </div>

        <!-- Academic Stats -->
        <div class="bento-item academic-stats" data-section="academic">
          <AcademicStats />
        </div>

        <!-- Projects Grid - Span full width -->
        <div class="bento-item projects-grid" data-section="projects">
          <ProjectsGrid />
        </div>

        <!-- Contact Card -->
        <div class="bento-item contact-card" data-section="contact">
          <ContactCard />
        </div>
      </div>

      <!-- Experience Timeline Section -->
      <div class="experience-section-wrapper">
        <ExperienceTimeline />
      </div>

      <!-- Chatbot Widget -->
      <ChatbotPlaceholder />

      <!-- Footer -->
      <footer class="site-footer" data-section="footer">
        <div class="footer-inner">
          <div class="footer-brand">
            <div class="footer-logo">
              <i class="fas fa-code"></i>
              <span>Phạm Duy Anh</span>
            </div>
            <p>Building thoughtful web experiences with Vue, modern UI, and a focus on clean execution.</p>
          </div>

          <div class="footer-links">
            <a href="#home" @click.prevent="scrollToSection('home')">Home</a>
            <a href="#experience" @click.prevent="scrollToSection('experience')">Experience</a>
            <a href="#projects" @click.prevent="scrollToSection('projects')">Projects</a>
            <a href="#contact" @click.prevent="scrollToSection('contact')">Contact</a>
          </div>

          <div class="footer-copy">
            <span>© 2026 Phạm Duy Anh</span>
            <span>Designed and built with Vue 3</span>
          </div>
        </div>
      </footer>
    </main>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import Navbar from '../components/Navbar.vue'
import HeroCard from '../components/HeroCard.vue'
import AcademicStats from '../components/AcademicStats.vue'
import ExperienceTimeline from '../components/ExperienceTimeline.vue'
import TechStack from '../components/TechStack.vue'
import ProjectsGrid from '../components/ProjectsGrid.vue'
import ContactCard from '../components/ContactCard.vue'
import ChatbotPlaceholder from '../components/ChatbotPlaceholder.vue'

const scrollToSection = (sectionId) => {
  const element = document.querySelector(`[data-section="${sectionId}"]`)
  if (element) {
    const navbarHeight = 80
    const targetTop = element.getBoundingClientRect().top + window.scrollY - navbarHeight
    window.scrollTo({ top: targetTop, behavior: 'smooth' })
  }
}

onMounted(async () => {
  await new Promise(resolve => setTimeout(resolve, 0))

  requestAnimationFrame(() => {
    if (window.AOS) {
      window.AOS.init({
        duration: 800,
        easing: 'ease-in-out-cubic',
        once: false,
        mirror: true,
        offset: 100
      })
    }

    if (window.AOS) {
      window.AOS.refresh()
    }
  })
})
</script>

<style scoped>
.portfolio-page {
  width: 100%;
  min-height: 100vh;
  background: var(--dark-bg);
}

.portfolio-main {
  position: relative;
  width: 100%;
  min-height: 100vh;
  padding: 100px 0 2rem 0;
  overflow-x: hidden;
}

/* Background Decorations - Gradient Orbs */
.background-decorations {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  pointer-events: none;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.1;
  animation: float 20s ease-in-out infinite;
}

.gradient-orb-1 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #a78bfa 0%, #60a5fa 100%);
  top: -100px;
  left: -100px;
  animation-delay: 0s;
}

.gradient-orb-2 {
  width: 300px;
  height: 300px;
  background: linear-gradient(135deg, #60a5fa 0%, #06b6d4 100%);
  bottom: 100px;
  right: 50px;
  animation-delay: 5s;
}

.gradient-orb-3 {
  width: 350px;
  height: 350px;
  background: linear-gradient(135deg, #06b6d4 0%, #a78bfa 100%);
  bottom: 0;
  left: 30%;
  animation-delay: 10s;
}

@keyframes float {
  0%, 100% {
    transform: translate(0, 0);
  }
  33% {
    transform: translate(50px, -50px);
  }
  66% {
    transform: translate(-30px, 30px);
  }
}

/* Content relative to background */
.bento-grid {
  position: relative;
  z-index: 1;
}

.academic-stats {
  grid-column: span 1;
  grid-row: span 1;
}

/* Experience Section Wrapper */
.experience-section-wrapper {
  position: relative;
  z-index: 1;
  width: 100%;
  background: rgba(15, 23, 42, 0.4);
  backdrop-filter: blur(10px);
  border-top: 1px solid rgba(167, 139, 250, 0.1);
  border-bottom: 1px solid rgba(167, 139, 250, 0.1);
  margin: 2rem 0;
}

/* Site Footer */
.site-footer {
  position: relative;
  z-index: 1;
  width: 100%;
  padding: 2rem 1.5rem 3rem;
  border-top: 1px solid rgba(167, 139, 250, 0.12);
  background: linear-gradient(180deg, rgba(10, 14, 39, 0.2) 0%, rgba(10, 14, 39, 0.85) 100%);
}

.footer-inner {
  max-width: 1400px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr;
  gap: 1.5rem;
  align-items: start;
}

.footer-brand p {
  margin: 0.75rem 0 0;
  color: var(--text-secondary);
  line-height: 1.7;
  max-width: 32rem;
}

.footer-logo {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
}

.footer-logo i {
  color: var(--primary-color);
}

.footer-links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer-links a {
  color: var(--text-secondary);
  text-decoration: none;
  transition: color 0.3s ease, transform 0.3s ease;
}

.footer-links a:hover {
  color: var(--primary-color);
  transform: translateX(4px);
}

.footer-copy {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  color: var(--text-secondary);
  text-align: right;
}

/* Desktop Responsiveness */
@media (max-width: 1200px) {
  .portfolio-main {
    padding: 90px 0 2rem 0;
  }

  .gradient-orb {
    filter: blur(60px);
  }

  .gradient-orb-1 {
    width: 300px;
    height: 300px;
  }

  .gradient-orb-2 {
    width: 250px;
    height: 250px;
  }

  .gradient-orb-3 {
    width: 280px;
    height: 280px;
  }
}

/* Tablet */
@media (max-width: 768px) {
  .portfolio-main {
    padding: 80px 0 2rem 0;
  }

  .gradient-orb {
    filter: blur(50px);
    opacity: 0.08;
  }

  .gradient-orb-1 {
    width: 200px;
    height: 200px;
    top: -50px;
    left: -50px;
  }

  .gradient-orb-2 {
    width: 180px;
    height: 180px;
    bottom: 50px;
    right: 20px;
  }

  .gradient-orb-3 {
    width: 200px;
    height: 200px;
  }

  .academic-stats {
    grid-column: span 1;
    grid-row: span 1;
  }

  .footer-inner {
    grid-template-columns: 1fr;
  }

  .footer-copy {
    text-align: left;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .portfolio-main {
    padding: 70px 0 1.5rem 0;
  }

  .gradient-orb {
    filter: blur(40px);
    opacity: 0.06;
  }

  .gradient-orb-1,
  .gradient-orb-2,
  .gradient-orb-3 {
    width: 150px;
    height: 150px;
  }

  .academic-stats {
    grid-column: span 1;
    grid-row: span 1;
  }

  .site-footer {
    padding: 1.5rem 1rem 2rem;
  }
}
</style>
