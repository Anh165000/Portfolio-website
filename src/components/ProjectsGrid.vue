<template>
  <div class="projects-content">
    <h3 class="mb-3">Featured Projects</h3>
    
    <!-- Loading State -->
    <div v-if="loading" class="loading-state">
      <div class="loader"></div>
      <p>Fetching projects from GitHub...</p>
    </div>

    <!-- Error State -->
    <div v-else-if="error" class="error-state">
      <i class="fas fa-exclamation-triangle"></i>
      <p>{{ error }}</p>
    </div>

    <!-- Projects List -->
    <div v-else class="projects-list">
      <div 
        v-for="(project, index) in projects"
        :key="project.id"
        class="project-card"
      >
        <div class="project-header">
          <i :class="getProjectIcon(project.language)"></i>
          <h4>{{ project.title }}</h4>
        </div>
        <p class="project-description">{{ project.description || 'No description provided' }}</p>
        <div class="project-meta">
          <span v-if="project.language" class="language-badge">
            <i class="fas fa-code"></i>
            {{ project.language }}
          </span>
          <span class="stars-badge">
            <i class="fas fa-star"></i>
            {{ project.stars }}
          </span>
        </div>
        <a :href="project.link" target="_blank" rel="noopener noreferrer" class="project-link">
          <i class="fab fa-github"></i>
          View on GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const projects = ref([])
const loading = ref(true)
const error = ref(null)
const GITHUB_USERNAME = 'anh1650000'

const languageIconMap = {
  'JavaScript': 'fab fa-js-square',
  'Python': 'fab fa-python',
  'Vue': 'fab fa-vuejs',
  'React': 'fab fa-react',
  'TypeScript': 'fab fa-js-square',
  'HTML': 'fab fa-html5',
  'CSS': 'fab fa-css3',
  'C++': 'fas fa-code',
  'Java': 'fab fa-java',
  'PHP': 'fab fa-php'
}

const getProjectIcon = (language) => {
  if (!language) return 'fas fa-laptop-code'
  return languageIconMap[language] || 'fas fa-laptop-code'
}

const fetchGitHubProjects = async () => {
  try {
    loading.value = true
    error.value = null

    const response = await fetch(
      `https://api.github.com/users/${GITHUB_USERNAME}/repos?sort=updated&per_page=6`
    )

    if (!response.ok) {
      throw new Error('Failed to fetch GitHub repositories')
    }

    const data = await response.json()

    // Transform GitHub API response to our project format
    projects.value = data.map((repo) => ({
      id: repo.id,
      title: repo.name,
      description: repo.description,
      language: repo.language,
      stars: repo.stargazers_count,
      link: repo.html_url,
      updated: repo.updated_at
    }))

    loading.value = false
  } catch (err) {
    console.error('Error fetching GitHub projects:', err)
    error.value = 'Unable to load projects from GitHub. Please try again later.'
    loading.value = false
  }
}

onMounted(() => {
  // Fetch GitHub projects
  fetchGitHubProjects()
})
</script>

<style scoped>
.projects-content {
  width: 100%;
}

h3 {
  text-align: left;
  margin-bottom: 1.5rem;
  margin: 0 0 1.5rem 0;
  font-size: 1.5rem;
  font-weight: 600;
}

/* Loading State */
.loading-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 3rem;
  gap: 1rem;
}

.loader {
  width: 40px;
  height: 40px;
  border: 4px solid rgba(167, 139, 250, 0.2);
  border-top-color: var(--primary-color);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.loading-state p {
  color: var(--text-secondary);
  font-size: 0.9rem;
}

/* Error State */
.error-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  gap: 1rem;
  background: rgba(239, 68, 68, 0.1);
  border: 1px solid rgba(239, 68, 68, 0.3);
  border-radius: 1rem;
}

.error-state i {
  font-size: 2rem;
  color: #ef4444;
}

.error-state p {
  color: var(--text-secondary);
  text-align: center;
}

/* Projects List */
.projects-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

.project-card {
  background: rgba(167, 139, 250, 0.03);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 1rem;
  padding: 1.5rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  display: flex;
  flex-direction: column;
  gap: 1rem;
  transform-style: preserve-3d;
}

.project-card:hover {
  border-color: var(--accent-color);
  box-shadow: 0 0 25px rgba(249, 115, 22, 0.3);
  transform: translateY(-5px);
}

.project-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.project-header i {
  font-size: 1.5rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.project-header h4 {
  font-size: 1.1rem;
  color: var(--text-primary);
  margin: 0;
  font-weight: 600;
}

.project-description {
  font-size: 0.95rem;
  color: var(--text-secondary);
  flex-grow: 1;
  margin: 0;
  line-height: 1.5;
}

.project-meta {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.language-badge,
.stars-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.35rem 0.75rem;
  background: rgba(167, 139, 250, 0.1);
  border: 1px solid rgba(167, 139, 250, 0.3);
  border-radius: 0.5rem;
  font-size: 0.75rem;
  color: var(--primary-color);
  font-weight: 600;
  transition: all 0.3s ease;
}

.language-badge i,
.stars-badge i {
  font-size: 0.8rem;
}

.language-badge:hover,
.stars-badge:hover {
  background: rgba(167, 139, 250, 0.2);
  border-color: var(--primary-color);
}

.project-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--accent-color);
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  margin-top: 0.5rem;
  width: fit-content;
}

.project-link:hover {
  gap: 0.75rem;
  color: var(--secondary-color);
}

.project-link i {
  transition: transform 0.3s ease;
}

.project-link:hover i {
  transform: rotate(-45deg) scale(1.2);
}

@media (max-width: 1024px) {
  .projects-list {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.2rem;
  }
}

@media (max-width: 768px) {
  .projects-list {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .project-card {
    padding: 1.2rem;
  }

  .project-header h4 {
    font-size: 1rem;
  }

  .project-description {
    font-size: 0.9rem;
  }
}
</style>
