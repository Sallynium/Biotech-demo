<template>
  <section class="section news-section" id="news">
    <div class="container">
      <div class="news-top">
        <div>
          <div class="section-label">最新消息</div>
          <h2 class="section-title">科技前沿<span class="highlight">動態</span></h2>
        </div>
        <a href="#" class="btn btn-outline">查看全部新聞</a>
      </div>

      <div class="news-grid">
        <div class="news-featured">
          <div class="news-card featured-card">
            <div class="news-img-placeholder featured-img">
              <div class="news-category-tag">重大突破</div>
              <div class="news-date-overlay">2026.02.28</div>
            </div>
            <div class="news-body">
              <div class="news-meta">
                <span class="news-cat">臨床試驗</span>
                <span class="news-date">2026 年 2 月 28 日</span>
              </div>
              <h3 class="news-title">BN-4271 CAR-T 療法在 Phase III 試驗中達到主要終點，多發性骨髓瘤患者 76% 達完全緩解</h3>
              <p class="news-excerpt">
                BioNova 今日宣布，其旗艦 CAR-T 產品 BN-4271 在全球 48 個試驗中心、
                納入 312 名患者的 Phase III 關鍵臨床試驗中，成功達到主要終點，展現出優越的臨床療效...
              </p>
              <a href="#" class="news-link">閱讀全文 →</a>
            </div>
          </div>
        </div>

        <div class="news-list">
          <div v-for="item in news" :key="item.title" class="news-card list-card">
            <div class="news-body">
              <div class="news-meta">
                <span class="news-cat" :style="{ background: item.catColor }">{{ item.category }}</span>
                <span class="news-date">{{ item.date }}</span>
              </div>
              <h3 class="news-title small">{{ item.title }}</h3>
              <a href="#" class="news-link">閱讀全文 →</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const news = [
  {
    category: '合作協議',
    date: '2026.02.15',
    catColor: 'rgba(127,255,212,0.15)',
    title: 'BioNova 與 Roche 簽署 8 億美元戰略合作協議，共同開發次世代 ADC 療法',
  },
  {
    category: '法規進展',
    date: '2026.01.30',
    catColor: 'rgba(0,200,150,0.15)',
    title: 'BN-Gene01 獲得 FDA 罕見兒科疾病認定，加速脊髓性肌肉萎縮症基因療法審查',
  },
  {
    category: '研究發表',
    date: '2026.01.18',
    catColor: 'rgba(10,79,110,0.4)',
    title: 'BioNova 研究團隊在 Nature Medicine 發表液態活檢早期癌症偵測突破性研究',
  },
  {
    category: '財務報告',
    date: '2025.12.05',
    catColor: 'rgba(127,255,212,0.15)',
    title: '2025 年第三季財報：營收增長 42%，研發管線持續擴展，現金儲備達 12 億美元',
  },
]
</script>

<style scoped>
.news-section {
  background: linear-gradient(180deg, rgba(10,79,110,0.08) 0%, var(--color-bg) 100%);
}

.news-top {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  margin-bottom: 48px;
  gap: 24px;
}

.news-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}

.news-card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  overflow: hidden;
  transition: all var(--transition);
}

.news-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-4px);
  box-shadow: 0 16px 48px rgba(0,0,0,0.4);
}

.news-img-placeholder {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, rgba(0,200,150,0.15), rgba(10,79,110,0.3));
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.news-img-placeholder::before {
  content: '🧬';
  font-size: 60px;
  opacity: 0.3;
}

.news-category-tag {
  position: absolute;
  top: 16px;
  left: 16px;
  padding: 6px 12px;
  background: var(--color-primary);
  color: #fff;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
}

.news-date-overlay {
  position: absolute;
  bottom: 16px;
  right: 16px;
  font-size: 12px;
  color: rgba(255,255,255,0.6);
}

.news-body {
  padding: 24px;
}

.news-meta {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}

.news-cat {
  font-size: 11px;
  padding: 4px 10px;
  border-radius: 20px;
  background: rgba(0, 200, 150, 0.15);
  color: var(--color-primary);
  font-weight: 600;
}

.news-date {
  font-size: 12px;
  color: var(--color-text-muted);
}

.news-title {
  font-size: 1.05rem;
  font-weight: 700;
  line-height: 1.5;
  margin-bottom: 12px;
}

.news-title.small {
  font-size: 0.95rem;
}

.news-excerpt {
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 16px;
}

.news-link {
  font-size: 13px;
  font-weight: 600;
  color: var(--color-primary);
  transition: color var(--transition);
}

.news-link:hover {
  color: var(--color-accent);
}

.news-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.list-card {
  display: flex;
}

.list-card .news-body {
  flex: 1;
  padding: 20px 24px;
}

@media (max-width: 768px) {
  .news-top {
    flex-direction: column;
    align-items: flex-start;
  }

  .news-grid {
    grid-template-columns: 1fr;
  }
}
</style>
