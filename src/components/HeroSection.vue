<template>
  <section class="hero">
    <!-- Animated background -->
    <div class="hero-bg">
      <div class="grid-overlay"></div>
      <div class="orb orb-1"></div>
      <div class="orb orb-2"></div>
      <div class="orb orb-3"></div>
      <canvas ref="dnaCanvas" class="dna-canvas"></canvas>
    </div>

    <div class="container hero-content">
      <div class="hero-text" :class="{ visible: mounted }">
        <div class="hero-badge">
          <span class="badge-dot"></span>
          正在進行 Phase III 臨床試驗
        </div>
        <h1 class="hero-title">
          用科學的力量<br />
          <span class="highlight">重新定義生命</span>
        </h1>
        <p class="hero-desc">
          BioNova 致力於基因療法、蛋白質工程與精準醫學，
          打造下一代創新生物科技解決方案，為人類帶來更健康的未來。
        </p>
        <div class="hero-actions">
          <a href="#research" class="btn btn-primary">
            探索研究領域
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
              <path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
          <a href="#products" class="btn btn-outline">查看產品管線</a>
        </div>
        <div class="hero-stats">
          <div v-for="stat in stats" :key="stat.label" class="stat">
            <span class="stat-value">{{ stat.value }}</span>
            <span class="stat-label">{{ stat.label }}</span>
          </div>
        </div>
      </div>

      <div class="hero-visual" :class="{ visible: mounted }">
        <div class="molecule-card">
          <div class="mol-ring mol-ring-1"></div>
          <div class="mol-ring mol-ring-2"></div>
          <div class="mol-ring mol-ring-3"></div>
          <div class="mol-core">
            <svg width="60" height="60" viewBox="0 0 60 60" fill="none">
              <circle cx="30" cy="30" r="18" stroke="#00C896" stroke-width="2" stroke-dasharray="4 4"/>
              <circle cx="30" cy="30" r="8" fill="rgba(0,200,150,0.2)" stroke="#00C896" stroke-width="2"/>
              <circle cx="30" cy="12" r="4" fill="#00C896"/>
              <circle cx="44" cy="38" r="4" fill="#7FFFD4"/>
              <circle cx="16" cy="38" r="4" fill="#0A4F6E" stroke="#00C896" stroke-width="1.5"/>
              <line x1="30" y1="22" x2="30" y2="16" stroke="#00C896" stroke-width="1.5"/>
              <line x1="38" y1="35" x2="44" y2="38" stroke="#7FFFD4" stroke-width="1.5"/>
              <line x1="22" y1="35" x2="16" y2="38" stroke="#00C896" stroke-width="1.5"/>
            </svg>
          </div>
          <div class="mol-label">基因分子結構模擬</div>
          <div class="mol-value">BN-4271 化合物</div>
        </div>

        <div class="data-cards">
          <div class="data-card" v-for="d in dataCards" :key="d.title">
            <div class="data-icon">{{ d.icon }}</div>
            <div class="data-info">
              <div class="data-value">{{ d.value }}</div>
              <div class="data-title">{{ d.title }}</div>
            </div>
            <div class="data-trend up">+{{ d.trend }}</div>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-indicator">
      <div class="scroll-line"></div>
      <span>向下探索</span>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const mounted = ref(false)
const dnaCanvas = ref(null)

const stats = [
  { value: '150+', label: '專利技術' },
  { value: '38', label: '臨床試驗' },
  { value: '12', label: '上市產品' },
  { value: '2,800+', label: '研究人員' },
]

const dataCards = [
  { icon: '🧬', title: '基因定序完成率', value: '98.7%', trend: '2.3%' },
  { icon: '💊', title: '藥物研發進度', value: 'Phase III', trend: '1 階段' },
]

onMounted(() => {
  setTimeout(() => { mounted.value = true }, 100)
  initDnaAnimation()
})

function initDnaAnimation() {
  const canvas = dnaCanvas.value
  if (!canvas) return
  const ctx = canvas.getContext('2d')

  const resize = () => {
    canvas.width = canvas.offsetWidth
    canvas.height = canvas.offsetHeight
  }
  resize()
  window.addEventListener('resize', resize)

  let t = 0
  const points = 20
  const amplitude = 60
  const speed = 0.02

  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height)
    const cx = canvas.width / 2
    const stepY = canvas.height / (points - 1)

    for (let i = 0; i < points - 1; i++) {
      const y1 = i * stepY
      const y2 = (i + 1) * stepY
      const phase = t + i * 0.4

      const x1L = cx + Math.sin(phase) * amplitude
      const x1R = cx - Math.sin(phase) * amplitude
      const x2L = cx + Math.sin(phase + 0.4) * amplitude
      const x2R = cx - Math.sin(phase + 0.4) * amplitude

      const alpha = 0.15 + 0.1 * Math.sin(phase)

      ctx.strokeStyle = `rgba(0, 200, 150, ${alpha})`
      ctx.lineWidth = 2
      ctx.beginPath()
      ctx.moveTo(x1L, y1)
      ctx.lineTo(x2L, y2)
      ctx.stroke()

      ctx.strokeStyle = `rgba(127, 255, 212, ${alpha})`
      ctx.beginPath()
      ctx.moveTo(x1R, y1)
      ctx.lineTo(x2R, y2)
      ctx.stroke()

      if (i % 3 === 0) {
        ctx.strokeStyle = `rgba(0, 200, 150, ${alpha * 1.5})`
        ctx.lineWidth = 1.5
        ctx.beginPath()
        ctx.moveTo(x1L, y1)
        ctx.lineTo(x1R, y1)
        ctx.stroke()

        ctx.fillStyle = `rgba(0, 200, 150, ${alpha * 2})`
        ctx.beginPath()
        ctx.arc(x1L, y1, 3, 0, Math.PI * 2)
        ctx.fill()
        ctx.beginPath()
        ctx.arc(x1R, y1, 3, 0, Math.PI * 2)
        ctx.fill()
      }
    }
    t += speed
    requestAnimationFrame(draw)
  }
  draw()
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  padding-top: 80px;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.grid-overlay {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(0, 200, 150, 0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 200, 150, 0.04) 1px, transparent 1px);
  background-size: 60px 60px;
}

.orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.35;
}

.orb-1 {
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(0,200,150,0.4), transparent);
  top: -200px;
  right: -100px;
  animation: float 8s ease-in-out infinite;
}

.orb-2 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(10,79,110,0.6), transparent);
  bottom: -100px;
  left: -100px;
  animation: float 10s ease-in-out infinite reverse;
}

.orb-3 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(127,255,212,0.2), transparent);
  top: 40%;
  left: 40%;
  animation: float 6s ease-in-out infinite 2s;
}

.dna-canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  opacity: 0.6;
}

.hero-content {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
  padding: 60px 24px;
}

.hero-text {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease;
}

.hero-text.visible {
  opacity: 1;
  transform: translateY(0);
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  background: rgba(0, 200, 150, 0.1);
  border: 1px solid rgba(0, 200, 150, 0.3);
  border-radius: 50px;
  font-size: 13px;
  color: var(--color-primary);
  font-weight: 500;
  margin-bottom: 24px;
}

.badge-dot {
  width: 8px;
  height: 8px;
  background: var(--color-primary);
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 24px;
}

.hero-desc {
  font-size: 1.1rem;
  color: var(--color-text-muted);
  line-height: 1.8;
  margin-bottom: 36px;
  max-width: 480px;
}

.hero-actions {
  display: flex;
  gap: 16px;
  margin-bottom: 48px;
  flex-wrap: wrap;
}

.hero-stats {
  display: flex;
  gap: 32px;
  flex-wrap: wrap;
}

.stat {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.stat-value {
  font-size: 1.8rem;
  font-weight: 800;
  background: linear-gradient(135deg, #fff, var(--color-primary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.stat-label {
  font-size: 12px;
  color: var(--color-text-muted);
  font-weight: 500;
}

/* Visual side */
.hero-visual {
  display: flex;
  flex-direction: column;
  gap: 20px;
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease 0.2s;
}

.hero-visual.visible {
  opacity: 1;
  transform: translateY(0);
}

.molecule-card {
  position: relative;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 16px;
  overflow: hidden;
}

.mol-ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid rgba(0, 200, 150, 0.15);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: spin linear infinite;
}

.mol-ring-1 { width: 200px; height: 200px; animation-duration: 20s; }
.mol-ring-2 { width: 300px; height: 300px; animation-duration: 30s; animation-direction: reverse; }
.mol-ring-3 { width: 400px; height: 400px; animation-duration: 40s; }

.mol-core {
  position: relative;
  z-index: 1;
  width: 100px;
  height: 100px;
  background: rgba(0, 200, 150, 0.05);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(0, 200, 150, 0.2);
}

.mol-label {
  font-size: 12px;
  color: var(--color-text-muted);
  position: relative;
  z-index: 1;
}

.mol-value {
  font-size: 16px;
  font-weight: 700;
  color: var(--color-primary);
  position: relative;
  z-index: 1;
}

.data-cards {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.data-card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius);
  padding: 20px;
  display: flex;
  align-items: center;
  gap: 12px;
  transition: all var(--transition);
}

.data-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(0, 200, 150, 0.15);
}

.data-icon {
  font-size: 28px;
}

.data-value {
  font-size: 1.1rem;
  font-weight: 700;
  color: var(--color-text);
}

.data-title {
  font-size: 11px;
  color: var(--color-text-muted);
  margin-top: 2px;
}

.data-trend {
  margin-left: auto;
  font-size: 12px;
  font-weight: 600;
  padding: 4px 8px;
  border-radius: 20px;
}

.data-trend.up {
  color: var(--color-primary);
  background: rgba(0, 200, 150, 0.1);
}

.scroll-indicator {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  color: var(--color-text-muted);
  font-size: 12px;
  z-index: 1;
  animation: bounce 2s ease-in-out infinite;
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, transparent, var(--color-primary));
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-30px); }
}

@keyframes spin {
  from { transform: translate(-50%, -50%) rotate(0deg); }
  to { transform: translate(-50%, -50%) rotate(360deg); }
}

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(1.3); }
}

@keyframes bounce {
  0%, 100% { transform: translateX(-50%) translateY(0); }
  50% { transform: translateX(-50%) translateY(8px); }
}

@media (max-width: 900px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-desc, .hero-actions, .hero-stats {
    justify-content: center;
  }

  .hero-visual {
    display: none;
  }
}
</style>
