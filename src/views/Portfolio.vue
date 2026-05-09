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
      <div class="experience-section-wrapper" data-section="experience">
        <ExperienceTimeline />
      </div>

      <!-- Chatbot Widget -->
      <ChatbotPlaceholder />

      <!-- Footer -->
      <footer class="site-footer" data-section="footer">
        <div class="footer-content">
          <!-- Contact Items -->
          <div class="footer-top">
            <div class="footer-contact-item">
              <div class="contact-icon">
                <i class="fas fa-phone"></i>
              </div>
              <p class="contact-label">Phone</p>
              <p class="contact-value">+84 834573195</p>
            </div>

            <div class="footer-contact-item">
              <div class="contact-icon">
                <i class="fas fa-envelope"></i>
              </div>
              <p class="contact-label">Receive emails at</p>
              <p class="contact-value">phamduyanh.01062005da@gmail.com</p>
            </div>

            <div class="footer-contact-item">
              <div class="contact-icon">
                <i class="fas fa-map-marker-alt"></i>
              </div>
              <p class="contact-label">Location</p>
              <p class="contact-value">Can Tho City, Vietnam</p>
            </div>
          </div>

          <!-- Bottom Footer -->
          <div class="footer-bottom">
            <div class="footer-copyright">
              <span>© 2026 Pham Duy Anh | Built with Vue 3 & Vite</span>
            </div>
            <div class="footer-socials">
              <a href="https://github.com/anh165000" target="_blank" rel="noopener noreferrer" title="Github">
                <i class="fab fa-github"></i>
              </a>
              <a href="https://www.instagram.com/phm.danhh__/" target="_blank" rel="noopener noreferrer" title="Instagram">
                <i class="fab fa-instagram"></i>
              </a>
              <a href="https://www.linkedin.com/in/duy-anh-ph%E1%BA%A1m-35ba53291/" target="_blank" rel="noopener noreferrer" title="LinkedIn">
                <i class="fab fa-linkedin"></i>
              </a>
              <a href="https://www.facebook.com/duyanhpham.165.000" target="_blank" rel="noopener noreferrer" title="Facebook">
                <i class="fab fa-facebook"></i>
              </a>
            </div>
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

onMounted(async () => {
  await new Promise(resolve => setTimeout(resolve, 0))

  requestAnimationFrame(() => {
    if (window.AOS) {
      window.AOS.init({
        duration: 400,
        once: true,
        disable: 'mobile',
        offset: 50
      })
    }

    if (window.AOS) {
      window.AOS.refresh()
    }

    // Vanilla Tilt disabled to prevent hover lag
    // Performance optimization: removed 3D tilt animation
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
  height: auto;
  min-height: 100vh;
  padding: 100px 0 0 0;
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
  /* border-bottom: 1px solid rgba(167, 139, 250, 0.1); */
  margin: 2rem 0;
}

/* Site Footer */
.site-footer {
  position: relative;
  z-index: 1;
  width: 100%;
  bottom: 0;
  margin-top: 3rem;
  background: linear-gradient(
    90deg,
    rgba(10, 14, 39, 0.8) 0%,
    rgba(10, 14, 39, 0.85) 25%,
    rgba(10, 14, 39, 0.95) 50%,
    rgba(10, 14, 39, 0.85) 75%,
    rgba(10, 14, 39, 0.8) 100%
  );
  color: var(--text-secondary);
}

.footer-content {
  position: relative;
  z-index: 1;
  padding: 3rem 1.5rem 2rem;
  /* background-color: rgba (10, 14, 39, 0.8); */
  bottom: 0;
  border-top: 1px solid rgba(167, 139, 250, 0.1);
}

.footer-top {
  max-width: 1400px;
  margin: 0 auto 2.5rem;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.footer-contact-item {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.75rem;
  color: rgba(255, 255, 255, 0.95);
}

.contact-icon {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
}

.contact-label {
  font-size: 0.9rem;
  opacity: 0.9;
  margin: 0;
  line-height: 1.4;
  color: rgba(255, 255, 255, 0.8);
}

.contact-value {
  font-size: 1rem;
  font-weight: 600;
  margin: 0;
  color: rgba(255, 255, 255, 0.95);
}

.footer-bottom {
  max-width: 1400px;
  margin: 0 auto;
  padding-top: 1.5rem;
  border-top: 1px solid rgba(167, 139, 250, 0.2);
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: rgba(255, 255, 255, 0.85);
}

.footer-copyright {
  font-size: 0.85rem;
}

.footer-socials {
  display: flex;
  gap: 1.25rem;
}

.footer-socials a {
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.2rem;
  text-decoration: none;
  transition: all 0.3s ease;
}

.footer-socials a:hover {
  color: var(--primary-color);
  transform: translateY(-3px);
}

/* Desktop Responsiveness */
@media (max-width: 1200px) {
  .portfolio-main {
    padding: 90px 0 0 0;
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
    padding: 80px 0 0 0;
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

  .footer-top {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }

  .footer-socials {
    justify-content: center;
  }
}

/* Mobile */
@media (max-width: 480px) {
  .portfolio-main {
    padding: 70px 0 0 0;
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
    padding: 0 1rem 2rem;
  }
}
</style>
