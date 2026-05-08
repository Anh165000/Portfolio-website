<template>
  <div class="tech-content" data-aos="fade-up">
    <h3>Tech Stack</h3>
    
    <div class="tech-grid">
      <div 
        v-for="tech in technologies"
        :key="tech.id"
        class="tech-item"
        :data-aos="'fade-up'"
        :data-aos-delay="tech.delay"
      >
        <i :class="tech.icon"></i>
        <p>{{ tech.name }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const technologies = [
  { id: 1, name: 'C++', icon: 'fas fa-code', delay: '0' },
  { id: 2, name: 'Python', icon: 'fab fa-python', delay: '100' },
  { id: 3, name: 'JavaScript', icon: 'fab fa-js-square', delay: '200' },
  { id: 4, name: 'Vue 3', icon: 'fab fa-vuejs', delay: '300' },
  { id: 5, name: 'Git', icon: 'fab fa-git-alt', delay: '400' }
]
</script>

<style scoped>
.tech-content {
  width: 100%;
}

h3 {
  text-align: center;
  margin-bottom: 1.5rem;
  margin: 0 0 1.5rem 0;
  font-size: 1.3rem;
  font-weight: 600;
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1rem;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1.2rem;
  background: rgba(167, 139, 250, 0.05);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 1rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  transform-style: preserve-3d;
}

.tech-item:hover {
  background: rgba(167, 139, 250, 0.15);
  border-color: var(--primary-color);
  box-shadow: 0 0 20px rgba(167, 139, 250, 0.3);
  transform: scale(1.1);
}

.tech-item i {
  font-size: 2rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
  transition: all 0.3s ease;
}

.tech-item:hover i {
  transform: scale(1.2);
}

.tech-item p {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--text-secondary);
  transition: color 0.3s ease;
  margin: 0;
}

.tech-item:hover p {
  color: var(--text-primary);
}

@media (max-width: 1024px) {
  .tech-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: 0.8rem;
  }

  .tech-item {
    padding: 1rem;
  }

  .tech-item i {
    font-size: 1.5rem;
  }
}

@media (max-width: 768px) {
  .tech-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: 0.6rem;
  }

  .tech-item {
    padding: 0.8rem;
  }

  .tech-item i {
    font-size: 1.3rem;
  }

  .tech-item p {
    font-size: 0.75rem;
  }
}

@media (max-width: 480px) {
  .tech-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 0.5rem;
  }

  .tech-item {
    padding: 0.6rem;
  }

  .tech-item i {
    font-size: 1.2rem;
  }

  .tech-item p {
    font-size: 0.7rem;
  }
}
</style>
