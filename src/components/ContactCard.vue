<template>
  <div class="contact-content" id="contact" data-aos="zoom-in">
    <h3>Get In Touch</h3>
    
    <!-- Status Badge -->
    <div class="status-badge">
      <i class="fas fa-circle"></i>
      <span>Available for Intern/Fresher roles</span>
    </div>
    
    <!-- Contact Description -->
    <p class="contact-description">
      Let's connect and collaborate on exciting projects!
    </p>

    <!-- Social Links -->
    <div class="social-links">
      <!-- GitHub -->
      <a 
        href="https://github.com/anh1650000"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
        title="GitHub"
      >
        <i class="fab fa-github"></i>
      </a>

      <!-- Facebook -->
      <a 
        href="https://www.facebook.com/duyanhpham.165.000"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
        title="Facebook"
      >
        <i class="fab fa-facebook"></i>
      </a>

      <!-- Email -->
      <a 
        href="mailto:phamduyanh.01062005da@gmail.com"
        class="social-btn"
        title="Email"
      >
        <i class="fas fa-envelope"></i>
      </a>

      <!-- LinkedIn -->
      <a 
        href="https://www.linkedin.com/in/duy-anh-ph%E1%BA%A1m-35ba53291"
        target="_blank"
        rel="noopener noreferrer"
        class="social-btn"
        title="LinkedIn"
      >
        <i class="fab fa-linkedin"></i>
      </a>
    </div>

    <!-- Copy Email Button -->
    <button class="copy-email-btn" @click="copyEmail" :title="copyTooltip">
      <i class="fas fa-copy"></i>
      {{ copyButtonText }}
    </button>

    <!-- Contact Info -->
    <div class="contact-info">
      <p><i class="fas fa-map-marker-alt"></i> Can Tho City, Viet Nam</p>
      <p><i class="fas fa-phone"></i> +84 834573195</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const copyButtonText = ref('Copy Email')
const copyTooltip = ref('Copy email address')
const email = 'phamduyanh.01062005da@gmail.com'

const copyEmail = async () => {
  try {
    await navigator.clipboard.writeText(email)
    copyButtonText.value = 'Copied!'
    copyTooltip.value = 'Email copied to clipboard!'
    setTimeout(() => {
      copyButtonText.value = 'Copy Email'
      copyTooltip.value = 'Copy email address'
    }, 2000)
  } catch (err) {
    console.error('Failed to copy email:', err)
  }
}
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

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: rgba(34, 197, 94, 0.1);
  border: 1px solid rgba(34, 197, 94, 0.3);
  border-radius: 2rem;
  font-size: 0.85rem;
  color: #22c55e;
  font-weight: 500;
  animation: pulse-badge 2s infinite;
}

.status-badge i {
  font-size: 0.5rem;
  animation: pulse-dot 2s infinite;
}

@keyframes pulse-dot {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.4;
  }
}

@keyframes pulse-badge {
  0%, 100% {
    background: rgba(34, 197, 94, 0.1);
  }
  50% {
    background: rgba(34, 197, 94, 0.15);
  }
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

.copy-email-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background: rgba(167, 139, 250, 0.15);
  border: 1px solid rgba(167, 139, 250, 0.4);
  border-radius: 0.75rem;
  color: var(--primary-color);
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 600;
  font-family: "Plus Jakarta Sans", sans-serif;
  font-size: 0.9rem;
}

.copy-email-btn:hover {
  background: var(--primary-color);
  color: var(--dark-bg);
  border-color: var(--primary-color);
  box-shadow: 0 5px 15px rgba(167, 139, 250, 0.4);
  transform: translateY(-2px);
}

.copy-email-btn i {
  transition: transform 0.3s ease;
}

.copy-email-btn:hover i {
  transform: rotate(15deg) scale(1.1);
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

  .status-badge {
    font-size: 0.8rem;
    padding: 0.4rem 0.8rem;
  }

  .social-btn {
    width: 45px;
    height: 45px;
    font-size: 1rem;
  }

  .contact-description {
    font-size: 0.9rem;
  }

  .copy-email-btn {
    padding: 0.6rem 1.2rem;
    font-size: 0.8rem;
  }
}
</style>
