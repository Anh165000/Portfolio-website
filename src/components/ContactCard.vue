<template>
  <div class="contact-content" data-aos="zoom-in">
    <h3>Get In Touch</h3>
    
    <!-- Contact Description -->
    <p class="contact-description">
      Let's connect and collaborate on exciting projects!
    </p>

    <!-- Social Links -->
    <div class="social-links">
      <!-- GitHub -->
      <a 
        href="https://github.com"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
        title="GitHub"
      >
        <i class="fab fa-github"></i>
      </a>

      <!-- Facebook -->
      <a 
        href="https://facebook.com"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
        title="Facebook"
      >
        <i class="fab fa-facebook"></i>
      </a>

      <!-- Email -->
      <a 
        href="mailto:phamduyanhdev@example.com"
        class="social-btn"
        title="Email"
      >
        <i class="fas fa-envelope"></i>
      </a>
    </div>

    <!-- Contact Info -->
    <div class="contact-info">
      <p><i class="fas fa-map-marker-alt"></i> Vietnam</p>
      <p><i class="fas fa-phone"></i> +84 123 456 789</p>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.contact-content {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  gap: 1rem;
}

h3 {
  font-size: 1.3rem;
  font-weight: 600;
  margin: 0;
}

.contact-description {
  color: var(--text-secondary);
  font-size: 0.9rem;
  margin: 0;
  line-height: 1.5;
}

.social-links {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.social-btn {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: rgba(167, 139, 250, 0.1);
  border: 1px solid rgba(167, 139, 250, 0.3);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--primary-color);
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  font-size: 1.2rem;
}

.social-btn:hover {
  background: var(--primary-color);
  color: var(--dark-bg);
  transform: translateY(-5px) scale(1.1);
  box-shadow: 0 5px 15px rgba(167, 139, 250, 0.4);
  border-color: var(--primary-color);
}

.social-btn i {
  transition: transform 0.3s ease;
}

.social-btn:hover i {
  transform: scale(1.2);
}

.contact-info {
  border-top: 1px solid rgba(167, 139, 250, 0.2);
  padding-top: 1.5rem;
  width: 100%;
}

.contact-info p {
  margin: 0.5rem 0;
  font-size: 0.9rem;
  color: var(--text-secondary);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.contact-info i {
  color: var(--primary-color);
  font-size: 1rem;
}

@media (max-width: 768px) {
  h3 {
    font-size: 1.3rem;
  }

  .social-btn {
    width: 45px;
    height: 45px;
    font-size: 1rem;
  }

  .contact-description {
    font-size: 0.9rem;
  }
}
</style>
