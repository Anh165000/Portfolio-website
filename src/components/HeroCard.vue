<template>
  <div class="hero-content" data-aos="fade-up">
    <!-- Avatar Placeholder -->
    <div class="avatar">
      <i class="fas fa-user-circle"></i>
    </div>

    <!-- Name -->
    <h1 class="hero-name">Phạm Duy Anh</h1>

    <!-- Typed.js Animation -->
    <div class="typed-container">
      <span ref="typedElement" class="typed-text"></span>
    </div>

    <!-- Major -->
    <p class="hero-major">
      <i class="fas fa-graduation-cap"></i>
      <span> 3-Year Computer Science Student</span>
    </p>

    <!-- Bio -->
    <p class="hero-bio">
      The whole world, or nothing at all.
    </p>

    <!-- Quick Stats -->
    <div class="stats-row">
      <div class="stat-item">
        <span class="stat-number">10+</span>
        <span class="stat-label">Projects</span>
      </div>
      <div class="stat-item">
        <span class="stat-number">5+</span>
        <span class="stat-label">Tech Stack</span>
      </div>
      <div class="stat-item">
        <span class="stat-number">100%</span>
        <span class="stat-label">Dedication</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const typedElement = ref(null)

onMounted(() => {
  // Initialize Typed.js for text animation
  if (window.Typed && typedElement.value) {
    new window.Typed(typedElement.value, {
      strings: [
        'AI Engineering Intern', 
        'Artificial Intelligence Researcher',
        'AI-Augmented Development Enthusiast',
        'Zero or One. No in-betweens.'
      ],
      typeSpeed: 50,
      backSpeed: 40,
      backDelay: 1500,
      loop: true,
      cursorChar: ''
    })
  }
})
</script>

<style scoped>
.hero-content {
  text-align: center;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 1.5rem 1rem;
  gap: 1rem;
}

.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  color: var(--dark-bg);
  animation: float 3s ease-in-out infinite;
  box-shadow: 0 0 30px rgba(167, 139, 250, 0.4);
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

.hero-name {
  font-size: 1.8rem;
  font-weight: 800;
  margin: 0.5rem 0 0 0;
  background: linear-gradient(135deg, var(--text-primary), var(--primary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.typed-container {
  font-size: 1.1rem;
  color: var(--primary-color);
  min-height: 1.5em;
  font-weight: 600;
  margin: 0.5rem 0;
}

.hero-major {
  font-size: 0.95rem;
  color: var(--secondary-color);
  margin: 0.5rem 0;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.hero-major i {
  font-size: 1rem;
}

.hero-bio {
  font-size: 0.85rem;
  color: var(--text-secondary);
  line-height: 1.5;
  margin: 0.5rem 0;
  max-width: 90%;
}

.stats-row {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
  margin-top: 1rem;
  width: 100%;
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 60px;
}

.stat-number {
  font-size: 1.25rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
}

.stat-label {
  font-size: 0.65rem;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-top: 0.25rem;
  white-space: nowrap;
}

/* Responsive */
@media (max-width: 768px) {
  .hero-content {
    padding: 1rem 0.75rem;
    gap: 0.8rem;
  }

  .hero-name {
    font-size: 1.5rem;
  }

  .typed-container {
    font-size: 1rem;
  }

  .avatar {
    width: 80px;
    height: 80px;
    font-size: 2.5rem;
  }

  .hero-bio {
    font-size: 0.8rem;
  }

  .stats-row {
    gap: 1rem;
  }

  .stat-number {
    font-size: 1rem;
  }

  .stat-label {
    font-size: 0.6rem;
  }
}

@media (max-width: 480px) {
  .hero-content {
    padding: 0.75rem 0.5rem;
    gap: 0.6rem;
  }

  .hero-name {
    font-size: 1.3rem;
  }

  .typed-container {
    font-size: 0.9rem;
  }

  .avatar {
    width: 70px;
    height: 70px;
    font-size: 2rem;
  }

  .hero-major {
    font-size: 0.85rem;
  }

  .hero-bio {
    font-size: 0.75rem;
    max-width: 95%;
  }

  .stats-row {
    gap: 0.8rem;
  }

  .stat-item {
    min-width: 50px;
  }

  .stat-number {
    font-size: 0.9rem;
  }

  .stat-label {
    font-size: 0.55rem;
  }
}
</style>
