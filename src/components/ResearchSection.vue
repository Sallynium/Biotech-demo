<template>
  <section class="section research-section" id="research">
    <div class="container">
      <div class="section-header">
        <div class="section-label">研究領域</div>
        <h2 class="section-title">突破界限的<span class="highlight">科學探索</span></h2>
        <p class="section-desc">
          我們在多個前沿生物科技領域進行深入研究，
          致力於將實驗室的科學發現轉化為能造福患者的真實療法。
        </p>
      </div>

      <div class="research-grid">
        <div
          v-for="(area, i) in researchAreas"
          :key="area.title"
          class="research-card"
          :class="{ featured: i === 0 }"
        >
          <div class="card-glow" :style="{ background: area.glow }"></div>
          <div class="card-icon">{{ area.icon }}</div>
          <div class="card-tag">{{ area.tag }}</div>
          <h3 class="card-title">{{ area.title }}</h3>
          <p class="card-desc">{{ area.desc }}</p>
          <div class="card-metrics">
            <div v-for="m in area.metrics" :key="m.label" class="metric">
              <span class="metric-value">{{ m.value }}</span>
              <span class="metric-label">{{ m.label }}</span>
            </div>
          </div>
          <a href="#" class="card-link">
            了解更多
            <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
              <path d="M2 7h10M8 3l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const researchAreas = [
  {
    icon: '🧬',
    tag: '核心技術',
    title: '基因療法',
    desc: '利用腺相關病毒（AAV）載體精準遞送治療基因，針對單基因遺傳疾病提供一次性根治方案。我們的 BN-Gene™ 平台已在多項試驗中展現卓越的安全性與有效性。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(0,200,150,0.2), transparent)',
    metrics: [
      { value: '12', label: '活躍計畫' },
      { value: '94%', label: '遞送效率' },
    ],
  },
  {
    icon: '🦠',
    tag: '細胞治療',
    title: 'CAR-T 細胞療法',
    desc: '工程化改造患者自身 T 細胞，使其能夠識別並摧毀癌細胞。我們的下一代 CAR-T 技術著重解決實體腫瘤治療的挑戰。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(127,255,212,0.15), transparent)',
    metrics: [
      { value: '76%', label: '完全緩解率' },
      { value: 'Phase III', label: '最高階段' },
    ],
  },
  {
    icon: '🔭',
    tag: '精準醫學',
    title: '生物標記與精準診斷',
    desc: '透過基因組學、蛋白質組學及人工智慧整合分析，開發高靈敏度液態活檢技術，實現癌症早期偵測與個人化治療方案制定。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(10,79,110,0.3), transparent)',
    metrics: [
      { value: '99.2%', label: '特異性' },
      { value: '早期 I/II', label: '偵測階段' },
    ],
  },
  {
    icon: '🧪',
    tag: '蛋白質工程',
    title: '抗體藥物偶聯物（ADC）',
    desc: '結合單株抗體的靶向性與細胞毒素的殺傷力，打造「智慧型導彈」，精準打擊腫瘤細胞而不傷害正常組織。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(0,160,122,0.2), transparent)',
    metrics: [
      { value: '8', label: '在研分子' },
      { value: '10x', label: '靶向倍率' },
    ],
  },
  {
    icon: '🧠',
    tag: '神經科學',
    title: '神經退化疾病治療',
    desc: '針對阿茲海默症、帕金森氏症等神經退化性疾病，開發能夠穿越血腦屏障的創新治療分子與基因靜默技術。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(0,200,150,0.15), transparent)',
    metrics: [
      { value: '5', label: '在研計畫' },
      { value: 'Phase I', label: '最高階段' },
    ],
  },
  {
    icon: '🤖',
    tag: 'AI 驅動',
    title: 'AI 藥物發現平台',
    desc: '整合機器學習與分子動力學模擬，加速識別高潛力候選藥物，將藥物發現週期從平均 5 年縮短至 18 個月。',
    glow: 'radial-gradient(circle at 30% 30%, rgba(127,255,212,0.12), transparent)',
    metrics: [
      { value: '70%', label: '週期縮短' },
      { value: '10B+', label: '分子資料庫' },
    ],
  },
]
</script>

<style scoped>
.research-section {
  background: linear-gradient(180deg, var(--color-bg) 0%, rgba(10,79,110,0.1) 50%, var(--color-bg) 100%);
}

.section-header {
  text-align: center;
  max-width: 680px;
  margin: 0 auto 64px;
}

.section-header .section-desc {
  margin: 0 auto;
}

.research-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.research-card {
  position: relative;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 32px;
  overflow: hidden;
  transition: all var(--transition);
}

.research-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-6px);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
}

.research-card.featured {
  grid-column: span 1;
  border-color: rgba(0, 200, 150, 0.4);
  background: linear-gradient(135deg, var(--color-bg-card), var(--color-bg-card2));
}

.card-glow {
  position: absolute;
  inset: 0;
  opacity: 0.5;
  transition: opacity var(--transition);
  pointer-events: none;
}

.research-card:hover .card-glow {
  opacity: 1;
}

.card-icon {
  font-size: 36px;
  margin-bottom: 16px;
}

.card-tag {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--color-primary);
  margin-bottom: 10px;
}

.card-title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 12px;
  position: relative;
}

.card-desc {
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 24px;
  position: relative;
}

.card-metrics {
  display: flex;
  gap: 24px;
  margin-bottom: 24px;
  padding: 16px;
  background: rgba(0, 0, 0, 0.2);
  border-radius: var(--radius);
  border: 1px solid rgba(0, 200, 150, 0.1);
  position: relative;
}

.metric {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.metric-value {
  font-size: 1.2rem;
  font-weight: 800;
  color: var(--color-primary);
}

.metric-label {
  font-size: 11px;
  color: var(--color-text-muted);
}

.card-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 14px;
  font-weight: 600;
  color: var(--color-primary);
  transition: gap var(--transition);
  position: relative;
}

.card-link:hover {
  gap: 10px;
}

@media (max-width: 1100px) {
  .research-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .research-grid {
    grid-template-columns: 1fr;
  }
}
</style>
