<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const goBack = () => {
  router.push('/')
}

const features = [
  { title: 'C# 스크립팅', desc: '객체 지향 프로그래밍으로 게임 로직 구현' },
  { title: 'Physics 엔진', desc: '2D/3D 실시간 물리 시뮬레이션' },
  { title: 'Animation', desc: 'Mecanim으로 복잡한 애니메이션 제어' },
  { title: 'UI System', desc: 'Canvas 기반 반응형 인터페이스' },
  { title: 'Rendering', desc: '고품질 실시간 렌더링 엔진' },
  { title: 'AR/VR', desc: '다양한 XR 플랫폼 통합 지원' }
]

const steps = [
  { num: '01', title: 'Unity Hub 설치', desc: '공식 사이트에서 Unity Hub 다운로드' },
  { num: '02', title: '에디터 설치', desc: '원하는 버전의 Unity 에디터 선택' },
  { num: '03', title: '프로젝트 생성', desc: '2D/3D 템플릿으로 프로젝트 시작' },
  { num: '04', title: '개발 시작', desc: 'C# 스크립트 작성 및 빌드' }
]
</script>

<template>
  <div class="learn">
    <nav class="nav">
      <div class="nav-content">
        <button class="back-btn" @click="goBack">← 뒤로</button>
        <span class="logo">Unity Dev</span>
      </div>
    </nav>

    <main class="content">
      <section class="intro-section">
        <h1 class="title">핵심 기능</h1>
        <p class="subtitle">Unity의 강력한 기능들을 알아보세요</p>
      </section>

      <section class="features-section">
        <div class="features-grid">
          <div v-for="(feature, idx) in features" :key="idx" class="feature-item">
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.desc }}</p>
          </div>
        </div>
      </section>

      <section class="steps-section">
        <h2 class="section-title">시작하기</h2>
        <div class="steps">
          <div v-for="(step, idx) in steps" :key="idx" class="step">
            <span class="step-num">{{ step.num }}</span>
            <div class="step-info">
              <h4>{{ step.title }}</h4>
              <p>{{ step.desc }}</p>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
.learn {
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
  display: flex;
  align-items: center;
  gap: 2rem;
}

.back-btn {
  background: none;
  border: none;
  color: #999;
  cursor: pointer;
  font-size: 1rem;
  transition: color 0.2s;
}

.back-btn:hover {
  color: #fff;
}

.logo {
  font-size: 1.2rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 8rem 2rem 4rem;
}

.intro-section {
  margin-bottom: 6rem;
}

.title {
  font-size: clamp(3rem, 6vw, 4rem);
  font-weight: 700;
  margin-bottom: 1rem;
  letter-spacing: -0.03em;
}

.subtitle {
  font-size: 1.2rem;
  color: #666;
}

.features-section {
  margin-bottom: 8rem;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 3rem 4rem;
}

.feature-item h3 {
  font-size: 1.3rem;
  margin-bottom: 0.8rem;
  font-weight: 600;
  letter-spacing: -0.01em;
}

.feature-item p {
  color: #666;
  line-height: 1.6;
}

.steps-section {
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2rem;
  margin-bottom: 3rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.steps {
  display: grid;
  gap: 2rem;
}

.step {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  padding: 2rem 0;
  border-bottom: 1px solid #1a1a1a;
}

.step:last-child {
  border-bottom: none;
}

.step-num {
  font-size: 1rem;
  color: #666;
  font-weight: 600;
  flex-shrink: 0;
}

.step-info h4 {
  font-size: 1.2rem;
  margin-bottom: 0.5rem;
  font-weight: 600;
  letter-spacing: -0.01em;
}

.step-info p {
  color: #666;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .nav-content {
    padding: 1rem;
  }
  
  .content {
    padding: 6rem 1.5rem 3rem;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .step {
    flex-direction: column;
    gap: 1rem;
  }
}
</style>
