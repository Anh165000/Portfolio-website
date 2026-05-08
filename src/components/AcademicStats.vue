<template>
  <div class="academic-content" data-aos="fade-up">
    <h3>Academic & Certifications</h3>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-ring" style="--progress: 92">
          <div class="stat-ring-inner">
            <span class="stat-value">3.7</span>
            <span class="stat-max">/ 4.0</span>
          </div>
        </div>
        <p class="stat-label">GPA</p>
      </div>

      <div class="stat-card">
        <div class="stat-ring" style="--progress: 70">
          <div class="stat-ring-inner">
            <span class="stat-value">7.0</span>
            <span class="stat-max">IELTS</span>
          </div>
        </div>
        <p class="stat-label">English</p>
      </div>

      <div class="stat-card stat-card-wide">
        <div class="award-badge">
          <i class="fas fa-award"></i>
        </div>
        <div>
          <p class="award-title">Sinh viên 5 tốt</p>
          <p class="award-subtitle">Programming contests & academic recognition</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.academic-content {
  width: 100%;
}

h3 {
  margin: 0 0 1.5rem;
  font-size: 1.3rem;
  font-weight: 600;
  text-align: center;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}

.stat-card,
.stat-card-wide {
  background: rgba(167, 139, 250, 0.06);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 1rem;
  padding: 1rem;
  backdrop-filter: blur(10px);
}

.stat-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.75rem;
}

.stat-card-wide {
  grid-column: 1 / -1;
  display: flex;
  align-items: center;
  gap: 1rem;
}

.stat-ring {
  width: 88px;
  height: 88px;
  border-radius: 50%;
  background: conic-gradient(var(--primary-color) calc(var(--progress) * 1%), rgba(167, 139, 250, 0.12) 0);
  display: grid;
  place-items: center;
}

.stat-ring-inner {
  width: 66px;
  height: 66px;
  border-radius: 50%;
  background: rgba(10, 14, 39, 0.95);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.stat-value {
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--text-primary);
  line-height: 1;
}

.stat-max {
  font-size: 0.65rem;
  color: var(--text-secondary);
  margin-top: 0.2rem;
}

.stat-label {
  margin: 0;
  font-size: 0.8rem;
  color: var(--text-secondary);
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.award-badge {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  display: grid;
  place-items: center;
  background: rgba(167, 139, 250, 0.12);
  color: var(--primary-color);
  flex-shrink: 0;
}

.award-badge i {
  font-size: 1.25rem;
}

.award-title {
  margin: 0;
  font-size: 0.95rem;
  font-weight: 700;
  color: var(--text-primary);
}

.award-subtitle {
  margin: 0.2rem 0 0;
  font-size: 0.8rem;
  color: var(--text-secondary);
  line-height: 1.5;
}

@media (max-width: 768px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }

  .stat-card-wide {
    flex-direction: row;
  }
}
</style>
