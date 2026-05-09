<template>
  <div class="experience-section" data-section="experience">
    <h2 class="section-title">Experience</h2>

    <div class="timeline-container">
      <div class="timeline-line"></div>

      <div
        v-for="(item, index) in experiences"
        :key="item.id"
        class="timeline-item"
      >
        <div class="timeline-dot">
          <div class="dot-inner"></div>
        </div>

        <div class="experience-card">
          <div class="years">
            {{ item.years }}
          </div>

          <h3 class="company-name">{{ item.company }}</h3>
          <p class="position">{{ item.position }}</p>
          <p class="description">{{ item.description }}</p>

          <div class="tech-badges">
            <span v-for="tech in item.technologies" :key="tech" class="badge">
              <i :class="getTechIcon(tech)"></i>
              <span class="badge-text">{{ tech }}</span>
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const experiences = ref([
  {
    id: 1,
    years: '2026 - Present',
    company: 'Freelance & Personal Projects',
    position: '',
    description: 'Working on personal projects and freelance gigs, honing skills in web development and AI engineering.',
    technologies: ['Python', 'Vue.js', 'MongoDB']
  },
  {
    id: 2,
    years: '2023 - 2027',
    company: 'Can Tho University',
    position: 'Computer Science Student',
    description: 'Studying computer science with a focus on machine learning, deep learning and algorithms.',
    technologies: ['Python', 'MySQL', 'Git']
  }
])

const techIconMap = {
  'Vue.js': 'fab fa-vuejs',
  'React': 'fab fa-react',
  'Node.js': 'fab fa-node',
  'JavaScript': 'fab fa-js-square',
  'Python': 'fab fa-python',
  'C++': 'fas fa-code',
  'MongoDB': 'fas fa-leaf',
  'PostgreSQL': 'fas fa-database',
  'Tailwind CSS': 'fas fa-palette',
  'Figma': 'fas fa-pen-nib',
  'SQL': 'fas fa-database',
  'Git': 'fab fa-git-alt'
}

const getTechIcon = (tech) => {
  return techIconMap[tech] || 'fas fa-tag'
}
</script>

<style scoped>
.experience-section {
  width: 100%;
  padding: 3rem 2rem;
  background: rgba(10, 14, 39, 0.55);
}

.section-title {
  text-align: center;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 3rem;
  background: linear-gradient(135deg, var(--text-primary) 0%, var(--primary-color) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.timeline-container {
  position: relative;
  width: 100%;
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 0 0;
}

.timeline-line {
  position: absolute;
  left: 1.25rem;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(
    180deg,
    var(--primary-color) 0%,
    var(--secondary-color) 50%,
    var(--primary-color) 100%
  );
  z-index: 1;
}

.timeline-item {
  position: relative;
  margin: 0 0 1.5rem 0;
  padding: 0 0 0 4rem;
  display: block;
  width: 100%;
}

.timeline-dot {
  position: absolute;
  left: 0.75rem;
  top: 1.1rem;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.dot-inner {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: var(--primary-color);
  box-shadow: 0 0 0 4px var(--dark-bg), 0 0 20px rgba(167, 139, 250, 0.6);
  animation: pulse-dot 2s ease-in-out infinite;
}

@keyframes pulse-dot {
  0%, 100% {
    transform: scale(1);
    box-shadow: 0 0 0 4px var(--dark-bg), 0 0 20px rgba(167, 139, 250, 0.6);
  }
  50% {
    transform: scale(1.3);
    box-shadow: 0 0 0 4px var(--dark-bg), 0 0 30px rgba(167, 139, 250, 0.8);
  }
}

.experience-card {
  display: block;
  width: 100%;
  padding: 1.5rem;
  background: rgba(15, 23, 42, 0.78);
  border: 1px solid rgba(167, 139, 250, 0.28);
  border-radius: 1rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  margin: 0;
  text-align: left;
  z-index: 2;
}

.experience-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(167, 139, 250, 0.05) 0%,
    rgba(96, 165, 250, 0.05) 100%
  );
  border-radius: 1rem;
  pointer-events: none;
}

.experience-card > * {
  position: relative;
  z-index: 1;
}

.experience-card:hover {
  border-color: var(--primary-color);
  background: rgba(15, 23, 42, 0.8);
  box-shadow: 0 0 20px rgba(167, 139, 250, 0.2);
  transform: translateY(-2px);
}

/* Years Badge */
.years {
  display: inline-block;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--secondary-color);
  background: rgba(96, 165, 250, 0.1);
  padding: 0.25rem 0.75rem;
  border-radius: 2rem;
  margin-bottom: 0.75rem;
}

/* Company Name */
.company-name {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.25rem;
}

/* Position */
.position {
  font-size: 0.95rem;
  color: var(--primary-color);
  font-weight: 500;
  margin-bottom: 0.75rem;
}

/* Description */
.description {
  font-size: 0.9rem;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1rem;
}

/* Tech Badges */
.tech-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 1rem;
}

.badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.4rem 0.8rem;
  background: rgba(167, 139, 250, 0.1);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 1rem;
  font-size: 0.75rem;
  color: var(--text-secondary);
  transition: all 0.3s ease;
}

.badge i {
  font-size: 0.85rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.badge-text {
  font-weight: 500;
}

.badge:hover {
  background: rgba(167, 139, 250, 0.2);
  border-color: var(--primary-color);
  color: var(--text-primary);
}

/* Responsive Design */
@media (max-width: 1024px) {
  .timeline-container {
    padding: 1.5rem 0 0;
  }

  .timeline-line {
    left: 1.25rem;
  }

  .timeline-item {
    padding-left: 3.5rem;
    width: 100%;
  }

  .timeline-dot {
    left: 0.5rem;
  }
}

@media (max-width: 768px) {
  .experience-section {
    padding: 1.5rem;
  }

  .section-title {
    font-size: 1.5rem;
    margin-bottom: 2rem;
  }

  .timeline-container {
    padding: 1rem 0 0;
  }

  .timeline-line {
    left: 1rem;
  }

  .timeline-item {
    padding-left: 3rem;
    margin-bottom: 1.5rem;
    width: 100%;
  }

  .timeline-dot {
    left: 0.35rem;
    top: 0.95rem;
  }

  .experience-card {
    padding: 1.25rem;
  }

  .company-name {
    font-size: 1.1rem;
  }

  .description {
    font-size: 0.85rem;
  }

  .tech-badges {
    gap: 0.4rem;
  }

  .badge {
    padding: 0.35rem 0.65rem;
    font-size: 0.7rem;
  }
}

@media (max-width: 480px) {
  .experience-section {
    padding: 1rem;
  }

  .section-title {
    font-size: 1.3rem;
    margin-bottom: 1.5rem;
  }

  .timeline-container {
    padding: 0.75rem 0 0;
  }

  .timeline-line {
    left: 0.85rem;
  }

  .timeline-item {
    padding-left: 2.7rem;
    margin-bottom: 1.25rem;
    width: 100%;
  }

  .timeline-dot {
    left: 0.2rem;
    top: 0.95rem;
  }

  .experience-card {
    padding: 1rem;
  }

  .company-name {
    font-size: 1rem;
  }

  .position {
    font-size: 0.85rem;
  }

  .description {
    font-size: 0.8rem;
  }

  .years {
    font-size: 0.65rem;
  }

  .tech-badges {
    gap: 0.3rem;
  }

  .badge {
    padding: 0.3rem 0.6rem;
    font-size: 0.65rem;
  }
}
</style>
