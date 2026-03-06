<template>
  <section class="section" id="about">
    <div class="container">
      <div class="about-grid">
        <div class="about-left" ref="leftRef">
          <div class="section-label">關於 BioNova</div>
          <h2 class="section-title">
            以創新科技<br />
            <span class="highlight">守護人類健康</span>
          </h2>
          <p class="section-desc">
            BioNova 成立於 2008 年，是亞太地區領先的生物科技公司。
            我們專注於基因療法、細胞治療及精準醫學，
            致力於開發能真正改變患者生命的突破性療法。
          </p>
          <p class="section-desc" style="margin-top: 16px;">
            透過與全球頂尖學術機構及醫院的深度合作，
            我們的研究覆蓋癌症、罕見病及神經退化性疾病等多個重要治療領域。
          </p>
          <div class="about-features">
            <div v-for="feat in features" :key="feat.title" class="about-feature">
              <div class="feat-icon">{{ feat.icon }}</div>
              <div>
                <div class="feat-title">{{ feat.title }}</div>
                <div class="feat-desc">{{ feat.desc }}</div>
              </div>
            </div>
          </div>
        </div>

        <div class="about-right" ref="rightRef">
          <div class="timeline">
            <div v-for="(item, i) in timeline" :key="item.year" class="timeline-item">
              <div class="tl-marker">
                <div class="tl-dot"></div>
                <div v-if="i < timeline.length - 1" class="tl-line"></div>
              </div>
              <div class="tl-content">
                <div class="tl-year">{{ item.year }}</div>
                <div class="tl-title">{{ item.title }}</div>
                <div class="tl-desc">{{ item.desc }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  { icon: '🔬', title: '尖端研究設施', desc: '配備最新儀器的 GMP 實驗室' },
  { icon: '🤝', title: '全球合作網絡', desc: '與 50+ 頂級機構建立夥伴關係' },
  { icon: '🏆', title: '業界認可', desc: '榮獲多項國際生技創新大獎' },
  { icon: '💡', title: '持續創新', desc: '每年投入營收 25% 於研發' },
]

const timeline = [
  { year: '2008', title: '公司創立', desc: '由三位頂尖科學家在台北共同創辦' },
  { year: '2012', title: '首個突破', desc: '完成首個基因療法平台 BN-Gene™ 開發' },
  { year: '2016', title: 'NASDAQ 上市', desc: '成功於那斯達克上市，募資 3.2 億美元' },
  { year: '2020', title: '亞太擴張', desc: '在新加坡、日本建立研發中心' },
  { year: '2024', title: '癌症療法突破', desc: 'CAR-T 療法獲 FDA 突破性療法認定' },
]
</script>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: start;
}

.about-features {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-top: 40px;
}

.about-feature {
  display: flex;
  gap: 14px;
  align-items: flex-start;
  padding: 18px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius);
  transition: all var(--transition);
}

.about-feature:hover {
  border-color: var(--color-primary);
  transform: translateY(-3px);
}

.feat-icon {
  font-size: 24px;
  flex-shrink: 0;
}

.feat-title {
  font-size: 14px;
  font-weight: 600;
  margin-bottom: 4px;
}

.feat-desc {
  font-size: 12px;
  color: var(--color-text-muted);
}

/* Timeline */
.timeline {
  position: relative;
}

.timeline-item {
  display: flex;
  gap: 20px;
}

.tl-marker {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-shrink: 0;
}

.tl-dot {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  background: var(--color-primary);
  border: 3px solid var(--color-bg);
  box-shadow: 0 0 0 2px var(--color-primary);
  flex-shrink: 0;
  margin-top: 4px;
}

.tl-line {
  width: 2px;
  flex-grow: 1;
  background: linear-gradient(to bottom, var(--color-primary), rgba(0,200,150,0.1));
  margin: 6px 0;
  min-height: 40px;
}

.tl-content {
  padding-bottom: 32px;
}

.tl-year {
  font-size: 12px;
  font-weight: 700;
  color: var(--color-primary);
  letter-spacing: 1px;
  margin-bottom: 4px;
}

.tl-title {
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 6px;
}

.tl-desc {
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.6;
}

@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .about-features {
    grid-template-columns: 1fr;
  }
}
</style>
