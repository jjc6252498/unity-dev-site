<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const goToLearn = () => {
  router.push('/learn')
}

const features = [
  { title: '멀티플랫폼', desc: '모바일, PC, 콘솔, 웹까지' },
  { title: '실시간 3D', desc: '고품질 렌더링 엔진' },
  { title: 'C# 기반', desc: '강력한 스크립팅' }
]
</script>

<template>
  <div class="home">
    <nav class="nav">
      <div class="nav-content">
        <span class="logo">Unity Dev</span>
      </div>
    </nav>

    <main class="hero">
      <div class="hero-content">
        <h1 class="hero-title">
          게임을 만드는<br>
          가장 강력한 방법
        </h1>
        <p class="hero-subtitle">
          Unity로 당신의 아이디어를 현실로 만드세요
        </p>
        
        <div class="features">
          <div v-for="(feature, idx) in features" :key="idx" class="feature">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.desc }}</p>
          </div>
        </div>

        <button class="cta-button" @click="goToLearn">
          시작하기
        </button>
      </div>
    </main>
  </div>
</template>

<style scoped>
.home {
  min-height: 100vh;
  background: #0a0a0a;
  color: #fff;
}

.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(10, 10, 10, 0.8);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.nav-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1.5rem 2rem;
}

.logo {
  font-size: 1.2rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 0 2rem;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.hero-title {
  font-size: clamp(3rem, 8vw, 5.5rem);
  font-weight: 700;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  letter-spacing: -0.03em;
}

.hero-subtitle {
  font-size: clamp(1.1rem, 2vw, 1.3rem);
  color: #999;
  margin-bottom: 4rem;
  max-width: 600px;
  font-weight: 400;
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
  max-width: 800px;
}

.feature {
  border-left: 2px solid #333;
  padding-left: 1.5rem;
  transition: border-color 0.3s ease;
}

.feature:hover {
  border-color: #fff;
}

.feature h3 {
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  letter-spacing: -0.01em;
}

.feature p {
  font-size: 0.95rem;
  color: #666;
  line-height: 1.5;
}

.cta-button {
  background: #fff;
  color: #0a0a0a;
  border: none;
  padding: 1rem 2.5rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
  letter-spacing: -0.01em;
}

.cta-button:hover {
  background: #e0e0e0;
  transform: translateY(-2px);
}

.cta-button:active {
  transform: translateY(0);
}

@media (max-width: 768px) {
  .nav-content {
    padding: 1rem;
  }
  
  .hero {
    padding: 0 1.5rem;
  }
  
  .features {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}
</style>
