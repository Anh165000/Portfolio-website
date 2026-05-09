<template>
  <nav class="navbar">
    <div class="navbar-container">
      <!-- Logo/Brand -->
      <div class="navbar-brand">
        <i class="fas fa-code"></i>
        <span>Phạm Duy Anh</span>
      </div>

      <!-- Navigation Links -->
      <div class="nav-links">
        <a href="#home" class="nav-link" @click.prevent="scrollToSection('home')">
          <span>Home</span>
          <!-- <i class="fas fa-home"></i> -->
        </a>
        <a href="#experience" class="nav-link" @click.prevent="scrollToSection('experience')">
          <span>Experience</span>
          <!-- <i class="fas fa-briefcase"></i> -->
        </a>
        <a href="#tech" class="nav-link" @click.prevent="scrollToSection('tech')">
          <span>Tech</span>
          <!-- <i class="fas fa-code"></i> -->
        </a>
        <a href="#projects" class="nav-link" @click.prevent="scrollToSection('projects')">
          <span>Projects</span>
          <!-- <i class="fas fa-folder"></i> -->
        </a>
        <a href="#contact" class="nav-link" @click.prevent="scrollToSection('contact')">
          <span>Contact</span>
          <!-- <i class="fas fa-envelope"></i> -->
        </a>
      </div>

      <!-- Mobile Menu Toggle -->
      <button class="mobile-toggle" @click="toggleMobileMenu">
        <i class="fas fa-bars"></i>
      </button>
    </div>

    <!-- Mobile Menu -->
    <transition name="slide-down">
      <div v-if="showMobileMenu" class="mobile-menu">
        <a href="#home" class="mobile-link" @click.prevent="scrollToSection('home')">Home</a>
        <a href="#experience" class="mobile-link" @click.prevent="scrollToSection('experience')">Experience</a>
        <a href="#tech" class="mobile-link" @click.prevent="scrollToSection('tech')">Tech</a>
        <a href="#projects" class="mobile-link" @click.prevent="scrollToSection('projects')">Projects</a>
        <a href="#contact" class="mobile-link" @click.prevent="scrollToSection('contact')">Contact</a>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const showMobileMenu = ref(false)

const toggleMobileMenu = () => {
  showMobileMenu.value = !showMobileMenu.value
}

const testScroll = () => {
  window.scrollTo({ top: 500, behavior: 'smooth' })
}

const scrollToSection = (sectionId) => {
  showMobileMenu.value = false
  
  setTimeout(() => {
    const element = document.querySelector(`[data-section="${sectionId}"]`)
    
    if (element) {
      const rect = element.getBoundingClientRect()
      const navbarHeight = 70
      const absoluteTop = rect.top + window.scrollY
      const targetScroll = absoluteTop - navbarHeight
      
      window.scrollTo({
        top: targetScroll,
        behavior: 'smooth'
      })
    }
  }, 50)
}

onMounted(() => {
  // Close mobile menu on window resize
  window.addEventListener('resize', () => {
    if (window.innerWidth > 768) {
      showMobileMenu.value = false
    }
  })
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 70px;
  background: rgba(10, 14, 39, 0.7);
  backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(167, 139, 250, 0.2);
  z-index: 1000;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.2);
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 100%;
}

.navbar-brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-size: 1.3rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.navbar-brand:hover {
  transform: scale(1.05);
}

.navbar-brand i {
  font-size: 1.5rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-links {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  position: relative;
  cursor: pointer;
  pointer-events: auto;
  user-select: none;
}

.nav-link:hover {
  color: var(--primary-color);
  background: rgba(167, 139, 250, 0.1);
  transform: translateY(-2px);
}

.nav-link i {
  font-size: 1rem;
  transition: all 0.3s ease;
}

.nav-link:hover i {
  transform: scale(1.2);
}

.mobile-toggle {
  display: none;
  background: none;
  border: none;
  color: var(--primary-color);
  font-size: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.mobile-toggle:hover {
  transform: scale(1.1);
}

.mobile-menu {
  position: absolute;
  top: 70px;
  left: 0;
  right: 0;
  background: rgba(10, 14, 39, 0.95);
  backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(167, 139, 250, 0.2);
  padding: 1rem 0;
  display: flex;
  flex-direction: column;
  gap: 0;
}

.mobile-link {
  display: block;
  padding: 1rem 2rem;
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  border-left: 3px solid transparent;
  cursor: pointer;
  pointer-events: auto;
  user-select: none;
}

.mobile-link:hover {
  background: rgba(167, 139, 250, 0.1);
  color: var(--primary-color);
  border-left-color: var(--primary-color);
  padding-left: calc(2rem + 6px);
}

@media (max-width: 768px) {
  .navbar {
    height: 60px;
  }

  .navbar-container {
    padding: 0 1.5rem;
  }

  .navbar-brand {
    font-size: 1.1rem;
  }

  .nav-links {
    display: none;
  }

  .mobile-toggle {
    display: block;
  }
}

.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}

.slide-down-enter-from {
  opacity: 0;
  transform: translateY(-20px);
}

.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
