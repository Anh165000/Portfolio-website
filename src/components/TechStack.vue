<template>
  <div class="tech-content" id="tech" data-aos="fade-up">
    <h3>Technical Proficiency</h3>
    
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
        <div class="proficiency">
          <div class="proficiency-bar">
            <div class="proficiency-fill" :style="{ width: tech.proficiency + '%' }"></div>
          </div>
          <span class="proficiency-label">{{ tech.proficiency }}%</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const technologies = [
  { id: 1, name: 'Python', icon: 'fab fa-python', proficiency: 80, delay: '0' },
  { id: 2, name: 'JavaScript', icon: 'fab fa-js-square', proficiency: 70, delay: '100' },
  { id: 3, name: 'Vue 3', icon: 'fab fa-vuejs', proficiency: 70, delay: '200' },
  { id: 4, name: 'Java', icon: 'fab fa-java', proficiency: 70, delay: '300' },
  { id: 5, name: 'C++', icon: 'fas fa-code', proficiency: 60, delay: '400' },
  { id: 6, name: 'Git', icon: 'fab fa-git-alt', proficiency: 95, delay: '500' }
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
  grid-template-columns: repeat(6, 1fr);
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
  margin: 0 0 0.75rem 0;
}

.tech-item:hover p {
  color: var(--text-primary);
}

.proficiency {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.4rem;
}

.proficiency-bar {
  width: 80%;
  height: 4px;
  background: rgba(167, 139, 250, 0.1);
  border-radius: 2px;
  overflow: hidden;
}

.proficiency-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  border-radius: 2px;
  transition: width 0.5s ease;
}

.proficiency-label {
  font-size: 0.7rem;
  color: var(--text-secondary);
  font-weight: 500;
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
