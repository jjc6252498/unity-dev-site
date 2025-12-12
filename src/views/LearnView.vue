<script setup>
import { useRouter } from 'vue-router'
import { ref } from 'vue'

const router = useRouter()

const goBack = () => {
  router.push('/')
}

const features = [
  { 
    title: 'C# 스크립팅', 
    desc: '객체 지향 프로그래밍으로 게임 로직 구현',
    icon: '💻',
    color: '#FF6B6B'
  },
  { 
    title: 'Physics 엔진', 
    desc: '2D/3D 실시간 물리 시뮬레이션',
    icon: '⚙️',
    color: '#4ECDC4'
  },
  { 
    title: 'Animation', 
    desc: 'Mecanim으로 복잡한 애니메이션 제어',
    icon: '🎬',
    color: '#FFE66D'
  },
  { 
    title: 'UI System', 
    desc: 'Canvas 기반 반응형 인터페이스',
    icon: '🎨',
    color: '#A8E6CF'
  },
  { 
    title: 'Rendering', 
    desc: '고품질 실시간 렌더링 엔진',
    icon: '✨',
    color: '#FFB6E1'
  },
  { 
    title: 'AR/VR', 
    desc: '다양한 XR 플랫폼 통합 지원',
    icon: '🥽',
    color: '#95E1D3'
  }
]

const steps = [
  { 
    num: '01', 
    title: 'Unity Hub 설치', 
    desc: '공식 사이트에서 Unity Hub 다운로드',
    color: '#FF6B6B'
  },
  { 
    num: '02', 
    title: '에디터 설치', 
    desc: '원하는 버전의 Unity 에디터 선택',
    color: '#4ECDC4'
  },
  { 
    num: '03', 
    title: '프로젝트 생성', 
    desc: '2D/3D 템플릿으로 프로젝트 시작',
    color: '#FFE66D'
  },
  { 
    num: '04', 
    title: '개발 시작', 
    desc: 'C# 스크립트 작성 및 빌드',
    color: '#A8E6CF'
  }
]
</script>

<template>
  <div class="learn">
    <div class="bg-gradient"></div>
    
    <div class="bg-shapes">
      <div class="shape shape-1"></div>
      <div class="shape shape-2"></div>
    </div>

    <nav class="nav">
      <div class="nav-content">
        <button class="back-btn" @click="goBack">
          <span class="arrow-back">←</span>
          <span>뒤로</span>
        </button>
        <span class="logo">Unity<span class="logo-accent">Dev</span></span>
      </div>
    </nav>

    <main class="content">
      <section class="intro-section">
        <div class="badge">💡 핵심 기능</div>
        <h1 class="title">
          <span class="gradient-text">Unity</span>의<br>
          강력한 기능들
        </h1>
        <p class="subtitle">전문가급 게임 개발을 위한 모든 것</p>
      </section>

      <section class="features-section">
        <div class="features-grid">
          <div 
            v-for="(feature, idx) in features" 
            :key="idx" 
            class="feature-card"
            :style="{ '--card-color': feature.color }"
          >
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.desc }}</p>
            <div class="card-shine"></div>
          </div>
        </div>
      </section>

      <section class="steps-section">
        <h2 class="section-title">시작하기</h2>
        <p class="section-subtitle">4단계로 간단하게 시작하세요</p>
        
        <div class="steps">
          <div 
            v-for="(step, idx) in steps" 
            :key="idx" 
            class="step-card"
            :style="{ '--step-color': step.color }"
          >
            <div class="step-number">{{ step.num }}</div>
            <div class="step-content">
              <h4>{{ step.title }}</h4>
              <p>{{ step.desc }}</p>
            </div>
            <div class="step-line"></div>
          </div>
        </div>
      </section>

      <section class="cta-section">
        <div class="cta-card">
          <h2>지금 바로 시작하세요</h2>
          <p>Unity로 당신의 게임 개발 여정을 시작하세요</p>
          <div class="cta-buttons">
            <button class="btn-primary">무료 다운로드</button>
            <button class="btn-secondary">문서 보기</button>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
.learn {
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
  background: radial-gradient(circle at 40% 40%, rgba(255, 107, 107, 0.1) 0%, transparent 50%),
              radial-gradient(circle at 60% 60%, rgba(78, 205, 196, 0.1) 0%, transparent 50%);
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
  filter: blur(80px);
  opacity: 0.2;
}

.shape-1 {
  width: 500px;
  height: 500px;
  background: linear-gradient(135deg, #FFE66D, #FFF19E);
  top: 20%;
  right: 10%;
  animation: float 25s infinite ease-in-out;
}

.shape-2 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, #A8E6CF, #C1F0E0);
  bottom: 10%;
  left: 5%;
  animation: float 20s infinite ease-in-out reverse;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50% { transform: translate(50px, -50px) scale(1.1); }
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
  align-items: center;
  justify-content: space-between;
}

.back-btn {
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.1);
  color: #fff;
  padding: 0.8rem 1.5rem;
  border-radius: 50px;
  cursor: pointer;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s;
  backdrop-filter: blur(10px);
}

.back-btn:hover {
  background: rgba(255, 255, 255, 0.15);
  transform: translateX(-5px);
}

.arrow-back {
  transition: transform 0.3s ease;
}

.back-btn:hover .arrow-back {
  transform: translateX(-3px);
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

.content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 10rem 3rem 6rem;
  position: relative;
  z-index: 1;
}

.intro-section {
  margin-bottom: 8rem;
  text-align: center;
}

.badge {
  display: inline-block;
  padding: 0.6rem 1.2rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-radius: 50px;
  font-size: 0.85rem;
  margin-bottom: 2rem;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.title {
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 800;
  margin-bottom: 2rem;
  letter-spacing: -0.02em;
  line-height: 1.2;
  word-break: keep-all;
}

.gradient-text {
  background: linear-gradient(135deg, #FF6B6B, #4ECDC4);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-size: 1.15rem;
  color: rgba(255, 255, 255, 0.75);
  margin-bottom: 1rem;
  line-height: 1.6;
}

.features-section {
  margin-bottom: 10rem;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.feature-card {
  position: relative;
  padding: 2.5rem;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  overflow: hidden;
}

.feature-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, var(--card-color) 0%, transparent 100%);
  opacity: 0;
  transition: opacity 0.4s ease;
}

.feature-card:hover {
  transform: translateY(-10px);
  background: rgba(255, 255, 255, 0.08);
  border-color: var(--card-color);
}

.feature-card:hover::before {
  opacity: 0.1;
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: block;
}

.feature-card h3 {
  font-size: 1.35rem;
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: -0.01em;
  position: relative;
  z-index: 1;
  word-break: keep-all;
}

.feature-card p {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.8);
  line-height: 1.7;
  position: relative;
  z-index: 1;
  word-break: keep-all;
}

.card-shine {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(45deg, transparent 30%, rgba(255, 255, 255, 0.1) 50%, transparent 70%);
  transform: translateX(-100%);
  transition: transform 0.6s;
}

.feature-card:hover .card-shine {
  transform: translateX(100%);
}

.steps-section {
  margin-bottom: 8rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 800;
  margin-bottom: 1.5rem;
  letter-spacing: -0.02em;
  text-align: center;
  word-break: keep-all;
}

.section-subtitle {
  text-align: center;
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.75);
  margin-bottom: 4rem;
  line-height: 1.6;
}

.steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.step-card {
  position: relative;
  padding: 2.5rem;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.step-card:hover {
  transform: translateY(-5px);
  background: rgba(255, 255, 255, 0.06);
  border-color: var(--step-color);
}

.step-number {
  font-size: 3.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--step-color), transparent);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1rem;
  line-height: 1;
}

.step-content h4 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: -0.01em;
  word-break: keep-all;
}

.step-content p {
  color: rgba(255, 255, 255, 0.8);
  line-height: 1.7;
  word-break: keep-all;
  font-size: 0.95rem;
}

.step-line {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--step-color), transparent);
  transition: width 0.4s ease;
}

.step-card:hover .step-line {
  width: 100%;
}

.cta-section {
  margin-bottom: 4rem;
}

.cta-card {
  background: linear-gradient(135deg, rgba(255, 107, 107, 0.1), rgba(78, 205, 196, 0.1));
  backdrop-filter: blur(20px);
  border-radius: 30px;
  padding: 4rem;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.2);
  position: relative;
  overflow: hidden;
}

.cta-card::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.05), transparent);
  animation: shimmer 3s infinite;
}

@keyframes shimmer {
  0% { transform: translateX(-100%) translateY(-100%) rotate(45deg); }
  100% { transform: translateX(100%) translateY(100%) rotate(45deg); }
}

.cta-card h2 {
  font-size: 2rem;
  font-weight: 800;
  margin-bottom: 1.5rem;
  letter-spacing: -0.02em;
  position: relative;
  z-index: 1;
  word-break: keep-all;
}

.cta-card p {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.8);
  margin-bottom: 2.5rem;
  position: relative;
  z-index: 1;
  line-height: 1.6;
  word-break: keep-all;
}

.cta-buttons {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
  position: relative;
  z-index: 1;
}

.btn-primary,
.btn-secondary {
  padding: 1.2rem 2.5rem;
  font-size: 1.05rem;
  font-weight: 600;
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary {
  background: linear-gradient(135deg, #FF6B6B, #FF8E8E);
  color: #fff;
  box-shadow: 0 10px 40px rgba(255, 107, 107, 0.3);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 15px 50px rgba(255, 107, 107, 0.4);
}

.btn-secondary {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  color: #fff;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.15);
  transform: translateY(-3px);
}

@media (max-width: 768px) {
  .nav-content {
    padding: 1rem 1.5rem;
  }
  
  .content {
    padding: 8rem 1.5rem 4rem;
  }
  
  .intro-section {
    margin-bottom: 5rem;
  }
  
  .features-grid,
  .steps {
    grid-template-columns: 1fr;
  }
  
  .cta-card {
    padding: 3rem 2rem;
  }
  
  .cta-buttons {
    flex-direction: column;
  }
  
  .btn-primary,
  .btn-secondary {
    width: 100%;
  }
}
</style>
