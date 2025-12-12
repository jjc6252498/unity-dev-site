<script setup>
import { useRouter } from 'vue-router'
import { ref, onMounted } from 'vue'

const router = useRouter()
const mouseX = ref(0)
const mouseY = ref(0)

const goToLearn = () => {
  router.push('/learn')
}

const features = [
  { 
    title: '멀티플랫폼', 
    desc: '모바일, PC, 콘솔, 웹까지',
    color: '#FF6B6B'
  },
  { 
    title: '실시간 3D', 
    desc: '고품질 렌더링 엔진',
    color: '#4ECDC4'
  },
  { 
    title: 'C# 기반', 
    desc: '강력한 스크립팅',
    color: '#FFE66D'
  }
]

const handleMouseMove = (e) => {
  mouseX.value = e.clientX / window.innerWidth
  mouseY.value = e.clientY / window.innerHeight
}

onMounted(() => {
  window.addEventListener('mousemove', handleMouseMove)
})
</script>

<template>
  <div class="home">
    <div class="bg-gradient" :style="{
      transform: `translate(${mouseX * 20}px, ${mouseY * 20}px)`
    }"></div>
    
    <div class="bg-shapes">
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
      <div class="shape shape-3"></div>
    </div>

    <nav class="nav">
      <div class="nav-content">
        <span class="logo">Unity<span class="logo-accent">Dev</span></span>
        <div class="nav-links">
          <a href="#" class="nav-link">소개</a>
          <a href="#" class="nav-link">기능</a>
        </div>
      </div>
    </nav>

    <main class="hero">
      <div class="hero-content">
        <div class="badge">🚀 게임 개발의 새로운 시작</div>
        
        <h1 class="hero-title">
          <span class="title-line">당신의 아이디어를</span>
          <span class="title-line gradient-text">현실로 만드는</span>
          <span class="title-line">가장 강력한 도구</span>
        </h1>
        
        <p class="hero-subtitle">
          Unity는 전세계 수백만 크리에이터들이 선택한<br>
          최고의 게임 개발 플랫폼입니다
        </p>
        
        <div class="cta-group">
          <button class="cta-button primary" @click="goToLearn">
            <span>자세히 알아보기</span>
            <span class="arrow">→</span>
          </button>
          <button class="cta-button secondary">
            <span>데모 보기</span>
          </button>
        </div>

        <div class="features">
          <div 
            v-for="(feature, idx) in features" 
            :key="idx" 
            class="feature-card"
            :style="{ '--accent-color': feature.color }"
          >
            <div class="feature-content">
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.desc }}</p>
            </div>
            <div class="feature-glow"></div>
          </div>
        </div>
      </div>
    </main>

    <div class="scroll-indicator">
      <span>스크롤</span>
      <div class="scroll-line"></div>
    </div>
  </div>
</template>

<style scoped>
.home {
  min-height: 100vh;
  background: #0f0f1e;
  color: #fff;
  position: relative;
  overflow: hidden;
}

.bg-gradient {
  position: fixed;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle at 30% 50%, rgba(255, 107, 107, 0.15) 0%, transparent 50%),
              radial-gradient(circle at 70% 50%, rgba(78, 205, 196, 0.15) 0%, transparent 50%),
              radial-gradient(circle at 50% 80%, rgba(255, 230, 109, 0.1) 0%, transparent 50%);
  transition: transform 0.3s ease-out;
  pointer-events: none;
}

.bg-shapes {
  position: fixed;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.shape {
  position: absolute;
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0.3;
  animation: float 20s infinite ease-in-out;
}

.shape-1 {
  width: 300px;
  height: 300px;
  background: linear-gradient(135deg, #FF6B6B, #FF8E8E);
  top: 10%;
  left: 10%;
  animation-delay: 0s;
}

.shape-2 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #4ECDC4, #6EE7E0);
  bottom: 20%;
  right: 10%;
  animation-delay: -7s;
}

.shape-3 {
  width: 250px;
  height: 250px;
  background: linear-gradient(135deg, #FFE66D, #FFF19E);
  top: 60%;
  left: 40%;
  animation-delay: -14s;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33% { transform: translate(30px, -30px) scale(1.1); }
  66% { transform: translate(-30px, 30px) scale(0.9); }
}

.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(15, 15, 30, 0.7);
  backdrop-filter: blur(20px) saturate(180%);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.nav-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 1.5rem 3rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  letter-spacing: -0.02em;
}

.logo-accent {
  background: linear-gradient(135deg, #FF6B6B, #4ECDC4);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-link {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-link:hover {
  color: #fff;
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 0 3rem;
  position: relative;
  z-index: 1;
}

.hero-content {
  max-width: 1400px;
  margin: 0 auto;
  width: 100%;
}

.badge {
  display: inline-block;
  padding: 0.6rem 1.2rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 50px;
  font-size: 0.85rem;
  margin-bottom: 3rem;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.hero-title {
  font-size: clamp(2.5rem, 7vw, 6rem);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 2rem;
  letter-spacing: -0.04em;
}

.title-line {
  display: block;
  animation: slideUp 0.8s ease-out backwards;
}

.title-line:nth-child(2) { animation-delay: 0.1s; }
.title-line:nth-child(3) { animation-delay: 0.2s; }

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
}

.gradient-text {
  background: linear-gradient(135deg, #FF6B6B 0%, #4ECDC4 50%, #FFE66D 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  background-size: 200% auto;
  animation: gradient-shift 3s ease infinite;
}

@keyframes gradient-shift {
  0%, 100% { background-position: 0% center; }
  50% { background-position: 100% center; }
}

.hero-subtitle {
  font-size: clamp(1.1rem, 2vw, 1.4rem);
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 3rem;
  line-height: 1.6;
  font-weight: 400;
}

.cta-group {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 5rem;
  flex-wrap: wrap;
}

.cta-button {
  padding: 1.2rem 2.5rem;
  font-size: 1.05rem;
  font-weight: 600;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.8rem;
  position: relative;
  overflow: hidden;
}

.cta-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, transparent 0%, rgba(255, 255, 255, 0.1) 100%);
  transform: translateX(-100%);
  transition: transform 0.6s ease;
}

.cta-button:hover::before {
  transform: translateX(0);
}

.cta-button.primary {
  background: linear-gradient(135deg, #FF6B6B, #FF8E8E);
  color: #fff;
  box-shadow: 0 10px 40px rgba(255, 107, 107, 0.3);
}

.cta-button.primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 15px 50px rgba(255, 107, 107, 0.4);
}

.cta-button.secondary {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.cta-button.secondary:hover {
  background: rgba(255, 255, 255, 0.15);
  transform: translateY(-3px);
}

.arrow {
  transition: transform 0.3s ease;
}

.cta-button:hover .arrow {
  transform: translateX(5px);
}

.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  max-width: 1200px;
}

.feature-card {
  position: relative;
  padding: 2rem;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
  overflow: hidden;
}

.feature-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, var(--accent-color), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.2);
}

.feature-card:hover::before {
  opacity: 1;
}

.feature-glow {
  position: absolute;
  width: 100px;
  height: 100px;
  background: var(--accent-color);
  border-radius: 50%;
  filter: blur(60px);
  opacity: 0;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.feature-card:hover .feature-glow {
  opacity: 0.2;
}

.feature-content {
  position: relative;
  z-index: 1;
}

.feature-card h3 {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 0.8rem;
  letter-spacing: -0.02em;
}

.feature-card p {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.7);
  line-height: 1.6;
}

.scroll-indicator {
  position: fixed;
  bottom: 3rem;
  left: 3rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  color: rgba(255, 255, 255, 0.5);
  font-size: 0.85rem;
  z-index: 10;
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, rgba(255, 255, 255, 0.5), transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { opacity: 0.5; transform: translateY(0); }
  50% { opacity: 1; transform: translateY(10px); }
}

@media (max-width: 768px) {
  .nav-content {
    padding: 1rem 1.5rem;
  }
  
  .nav-links {
    display: none;
  }
  
  .hero {
    padding: 0 1.5rem;
  }
  
  .badge {
    font-size: 0.75rem;
    padding: 0.5rem 1rem;
  }
  
  .features {
    grid-template-columns: 1fr;
  }
  
  .cta-group {
    flex-direction: column;
  }
  
  .cta-button {
    width: 100%;
    justify-content: center;
  }
  
  .scroll-indicator {
    display: none;
  }
}
</style>
