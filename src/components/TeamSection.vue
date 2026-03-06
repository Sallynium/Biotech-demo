<template>
  <section class="section team-section" id="team">
    <div class="container">
      <div class="section-header" style="text-align:center; max-width:600px; margin:0 auto 64px;">
        <div class="section-label">核心團隊</div>
        <h2 class="section-title">世界級的<span class="highlight">科學領袖</span></h2>
        <p class="section-desc" style="margin:0 auto;">
          我們的團隊匯聚了來自全球的頂尖科學家、醫師及業界領袖，
          共同推動生物科技的邊界。
        </p>
      </div>

      <div class="team-grid">
        <div v-for="member in team" :key="member.name" class="team-card">
          <div class="member-avatar" :style="{ background: member.gradient }">
            <span class="avatar-initials">{{ getInitials(member.name) }}</span>
            <div class="avatar-ring"></div>
          </div>
          <div class="member-info">
            <h3 class="member-name">{{ member.name }}</h3>
            <div class="member-role">{{ member.role }}</div>
            <div class="member-credentials">{{ member.credentials }}</div>
            <p class="member-bio">{{ member.bio }}</p>
            <div class="member-tags">
              <span v-for="tag in member.expertise" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="team-cta">
        <div class="cta-content">
          <h3>加入我們，共創未來</h3>
          <p>我們正在尋找充滿熱情的科學家和創新者</p>
        </div>
        <a href="#contact" class="btn btn-primary">查看職缺</a>
      </div>
    </div>
  </section>
</template>

<script setup>
const team = [
  {
    name: '陳明哲 博士',
    role: '創辦人暨執行長',
    credentials: 'MD, PhD — 哈佛醫學院',
    bio: '前 NIH 首席研究員，在基因療法領域擁有 20 年深厚經驗，發表超過 180 篇頂尖期刊論文。',
    gradient: 'linear-gradient(135deg, #00C896, #0A4F6E)',
    expertise: ['基因療法', '臨床轉化', '創業領導'],
  },
  {
    name: '林佳蓉 博士',
    role: '科學長（CSO）',
    credentials: 'PhD — MIT 生物工程學系',
    bio: '蛋白質工程與 ADC 技術專家，主導開發 BioNova 核心 ADC 平台，持有 35 項國際專利。',
    gradient: 'linear-gradient(135deg, #7FFFD4, #00A07A)',
    expertise: ['蛋白質工程', 'ADC', '藥物設計'],
  },
  {
    name: '王建國 教授',
    role: '醫學長（CMO）',
    credentials: 'MD — 史丹佛大學醫學院',
    bio: '腫瘤免疫學權威，曾主持超過 30 項國際多中心臨床試驗，在 CAR-T 療法領域享譽全球。',
    gradient: 'linear-gradient(135deg, #0A4F6E, #00C896)',
    expertise: ['腫瘤免疫', '臨床試驗', 'CAR-T'],
  },
  {
    name: '張慧玲 博士',
    role: '首席 AI 科學家',
    credentials: 'PhD — 劍橋大學計算生物學',
    bio: 'DeepMind 前研究員，專精於 AI 輔助藥物發現，主導建立 BioNova 的分子模擬與 AI 預測平台。',
    gradient: 'linear-gradient(135deg, #7FFFD4, #0A4F6E)',
    expertise: ['機器學習', '計算生物', '藥物發現'],
  },
]

function getInitials(name) {
  return name.slice(0, 2)
}
</script>

<style scoped>
.team-section {
  background: linear-gradient(180deg, var(--color-bg) 0%, rgba(5,13,26,0.95) 100%);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  margin-bottom: 48px;
}

.team-card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 32px;
  display: flex;
  gap: 24px;
  transition: all var(--transition);
}

.team-card:hover {
  border-color: var(--color-primary);
  transform: translateY(-4px);
  box-shadow: 0 16px 48px rgba(0, 0, 0, 0.4);
}

.member-avatar {
  position: relative;
  width: 80px;
  height: 80px;
  border-radius: 50%;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

.avatar-initials {
  font-size: 1.4rem;
  font-weight: 800;
  color: #fff;
  position: relative;
  z-index: 1;
}

.avatar-ring {
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  border: 2px solid rgba(0, 200, 150, 0.3);
  animation: spin 8s linear infinite;
}

.member-name {
  font-size: 1.1rem;
  font-weight: 700;
  margin-bottom: 4px;
}

.member-role {
  font-size: 14px;
  color: var(--color-primary);
  font-weight: 600;
  margin-bottom: 4px;
}

.member-credentials {
  font-size: 12px;
  color: var(--color-text-muted);
  margin-bottom: 12px;
}

.member-bio {
  font-size: 13px;
  color: var(--color-text-muted);
  line-height: 1.7;
  margin-bottom: 16px;
}

.member-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}

.tag {
  font-size: 11px;
  padding: 4px 10px;
  background: rgba(0, 200, 150, 0.1);
  border: 1px solid rgba(0, 200, 150, 0.2);
  border-radius: 20px;
  color: var(--color-primary);
  font-weight: 500;
}

.team-cta {
  background: linear-gradient(135deg, rgba(0,200,150,0.1), rgba(10,79,110,0.2));
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

.cta-content h3 {
  font-size: 1.4rem;
  font-weight: 700;
  margin-bottom: 8px;
}

.cta-content p {
  color: var(--color-text-muted);
}

@keyframes spin {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@media (max-width: 900px) {
  .team-grid {
    grid-template-columns: 1fr;
  }

  .team-card {
    flex-direction: column;
  }

  .team-cta {
    flex-direction: column;
    text-align: center;
  }
}
</style>
