<template>
  <div class="chatbot-wrapper">
    <!-- Floating Chatbot Button -->
    <button 
      class="chatbot-button"
      @click="toggleChat"
      :title="isOpen ? 'Close' : 'Open Chat'"
    >
      <i class="fas fa-comments"></i>
      <span v-if="!isOpen" class="pulse-badge"></span>
    </button>

    <!-- Chat Widget -->
    <transition name="slide-up">
      <div v-if="isOpen" class="chat-widget">
        <div class="chat-header">
          <h3>Quick Chat</h3>
          <button class="close-btn" @click="toggleChat">
            <i class="fas fa-times"></i>
          </button>
        </div>

        <div class="chat-body">
          <div class="welcome-message">
            <p>👋 Hi! I'm a chatbot assistant. Feel free to ask me anything!</p>
          </div>
        </div>

        <div class="chat-input">
          <input 
            type="text" 
            v-model="input" 
            @keyup.enter="sendMessage"
            placeholder="Type a message..."
          />
          <button @click="sendMessage">
            <i class="fas fa-paper-plane"></i>
          </button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isOpen = ref(false)
const input = ref('')

const toggleChat = () => {
  isOpen.value = !isOpen.value
}

const sendMessage = () => {
  if (input.value.trim()) {
    input.value = ''
  }
}
</script>

<style scoped>
.chatbot-wrapper {
  position: fixed;
  bottom: 4rem;
  right: 2rem;
  z-index: 999;
  font-family: 'Plus Jakarta Sans', sans-serif;
}

.chatbot-button {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  border: none;
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  box-shadow: 0 5px 20px rgba(167, 139, 250, 0.4);
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.chatbot-button:hover {
  transform: scale(1.1);
  box-shadow: 0 8px 30px rgba(167, 139, 250, 0.6);
}

.chatbot-button:active {
  transform: scale(0.95);
}

.pulse-badge {
  position: absolute;
  width: 15px;
  height: 15px;
  background: #ef4444;
  border-radius: 50%;
  top: -5px;
  right: -5px;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0% {
    box-shadow: 0 0 0 0 rgba(239, 68, 68, 0.7);
  }
  70% {
    box-shadow: 0 0 0 10px rgba(239, 68, 68, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(239, 68, 68, 0);
  }
}

.chat-widget {
  position: absolute;
  bottom: 80px;
  right: 0;
  width: 350px;
  height: 400px;
  background: var(--dark-card);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 1.25rem;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.chat-header {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}

.chat-header h3 {
  margin: 0;
  font-size: 1.1rem;
  font-weight: 600;
}

.close-btn {
  background: none;
  border: none;
  color: white;
  font-size: 1.2rem;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.close-btn:hover {
  transform: rotate(90deg);
}

.chat-body {
  flex: 1;
  overflow-y: auto;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.welcome-message {
  background: rgba(167, 139, 250, 0.1);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 0.75rem;
  padding: 1rem;
  color: var(--text-secondary);
}

.welcome-message p {
  margin: 0;
  font-size: 0.9rem;
  line-height: 1.5;
}

.chat-input {
  display: flex;
  gap: 0.5rem;
  padding: 1rem;
  border-top: 1px solid rgba(167, 139, 250, 0.2);
  background: rgba(10, 14, 39, 0.5);
}

.chat-input input {
  flex: 1;
  background: rgba(167, 139, 250, 0.05);
  border: 1px solid rgba(167, 139, 250, 0.2);
  border-radius: 0.5rem;
  padding: 0.6rem 0.75rem;
  color: var(--text-primary);
  font-family: inherit;
  font-size: 0.9rem;
  transition: all 0.3s ease;
}

.chat-input input:focus {
  outline: none;
  border-color: var(--primary-color);
  background: rgba(167, 139, 250, 0.1);
  box-shadow: 0 0 10px rgba(167, 139, 250, 0.2);
}

.chat-input button {
  background: var(--primary-color);
  border: none;
  border-radius: 0.5rem;
  color: var(--dark-bg);
  cursor: pointer;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  font-size: 1rem;
}

.chat-input button:hover {
  background: var(--secondary-color);
  transform: scale(1.05);
}

.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.3s ease;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateY(20px);
}

.slide-up-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

@media (max-width: 768px) {
  .chatbot-wrapper {
    bottom: 1rem;
    right: 1rem;
  }

  .chatbot-button {
    width: 50px;
    height: 50px;
    font-size: 1.2rem;
  }

  .chat-widget {
    width: 300px;
    height: 350px;
  }
}
</style>
