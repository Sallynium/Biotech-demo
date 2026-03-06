<template>
  <section class="section" id="products">
    <div class="container">
      <div class="section-header" style="text-align:center; max-width:680px; margin:0 auto 64px;">
        <div class="section-label">產品管線</div>
        <h2 class="section-title">從實驗室到<span class="highlight">臨床現場</span></h2>
        <p class="section-desc" style="margin:0 auto;">
          我們擁有豐富的藥物開發管線，橫跨多個治療領域，
          多項候選藥物已進入關鍵臨床試驗階段。
        </p>
      </div>

      <div class="pipeline-table">
        <div class="pipeline-header">
          <div class="ph-name">候選藥物</div>
          <div class="ph-indication">適應症</div>
          <div class="ph-modality">技術平台</div>
          <div class="ph-stages">開發階段</div>
        </div>

        <div
          v-for="drug in pipeline"
          :key="drug.name"
          class="pipeline-row"
          :class="{ highlighted: drug.highlighted }"
        >
          <div class="pd-name">
            <span class="drug-name">{{ drug.name }}</span>
            <span v-if="drug.badge" class="drug-badge">{{ drug.badge }}</span>
          </div>
          <div class="pd-indication">{{ drug.indication }}</div>
          <div class="pd-modality">
            <span class="modality-tag">{{ drug.modality }}</span>
          </div>
          <div class="pd-stages">
            <div class="stage-bars">
              <div
                v-for="(stage, i) in stages"
                :key="stage"
                class="stage-bar"
                :class="getStageClass(drug.stage, i)"
              >
                <div class="stage-fill"></div>
                <span class="stage-name">{{ stage }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="legend">
        <div class="legend-item">
          <div class="legend-dot active"></div>
          <span>進行中</span>
        </div>
        <div class="legend-item">
          <div class="legend-dot completed"></div>
          <span>已完成</span>
        </div>
        <div class="legend-item">
          <div class="legend-dot pending"></div>
          <span>規劃中</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const stages = ['Pre-IND', 'Phase I', 'Phase II', 'Phase III', '申請上市']

const pipeline = [
  {
    name: 'BN-4271',
    indication: '多發性骨髓瘤',
    modality: 'CAR-T 療法',
    stage: 3,
    badge: '突破性療法',
    highlighted: true,
  },
  {
    name: 'BN-Gene01',
    indication: '脊髓性肌肉萎縮症',
    modality: '基因療法',
    stage: 2,
    badge: null,
    highlighted: false,
  },
  {
    name: 'BN-ADC03',
    indication: 'HER2+ 乳癌',
    modality: 'ADC',
    stage: 2,
    badge: '孤兒藥認定',
    highlighted: false,
  },
  {
    name: 'BN-Neuro7',
    indication: '早發性阿茲海默症',
    modality: 'RNA 干擾',
    stage: 1,
    badge: null,
    highlighted: false,
  },
  {
    name: 'BN-T19',
    indication: '急性淋巴性白血病',
    modality: 'CAR-T 療法',
    stage: 2,
    badge: null,
    highlighted: false,
  },
  {
    name: 'BN-EYE2',
    indication: '利伯氏先天性黑矇症',
    modality: '基因療法',
    stage: 0,
    badge: null,
    highlighted: false,
  },
]

function getStageClass(currentStage, index) {
  if (index < currentStage) return 'completed'
  if (index === currentStage) return 'active'
  return 'pending'
}
</script>

<style scoped>
.pipeline-table {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  overflow: hidden;
}

.pipeline-header {
  display: grid;
  grid-template-columns: 220px 200px 160px 1fr;
  padding: 16px 28px;
  background: rgba(0, 200, 150, 0.06);
  border-bottom: 1px solid var(--color-border);
  font-size: 12px;
  font-weight: 600;
  color: var(--color-text-muted);
  letter-spacing: 1px;
  text-transform: uppercase;
}

.pipeline-row {
  display: grid;
  grid-template-columns: 220px 200px 160px 1fr;
  padding: 20px 28px;
  border-bottom: 1px solid rgba(0, 200, 150, 0.06);
  align-items: center;
  transition: all var(--transition);
}

.pipeline-row:last-child {
  border-bottom: none;
}

.pipeline-row:hover {
  background: rgba(0, 200, 150, 0.04);
}

.pipeline-row.highlighted {
  background: rgba(0, 200, 150, 0.05);
  border-left: 3px solid var(--color-primary);
}

.drug-name {
  font-size: 15px;
  font-weight: 700;
  display: block;
  margin-bottom: 4px;
}

.drug-badge {
  font-size: 11px;
  padding: 3px 8px;
  background: rgba(0, 200, 150, 0.15);
  color: var(--color-primary);
  border-radius: 20px;
  font-weight: 600;
}

.pd-indication {
  font-size: 14px;
  color: var(--color-text-muted);
}

.modality-tag {
  font-size: 12px;
  padding: 5px 12px;
  background: rgba(10, 79, 110, 0.4);
  border: 1px solid rgba(0, 200, 150, 0.2);
  border-radius: 20px;
  color: var(--color-text);
  font-weight: 500;
}

.stage-bars {
  display: flex;
  gap: 4px;
}

.stage-bar {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 4px;
  align-items: center;
}

.stage-fill {
  height: 8px;
  width: 100%;
  border-radius: 4px;
  background: rgba(255,255,255,0.05);
  transition: all var(--transition);
}

.stage-bar.completed .stage-fill {
  background: var(--color-primary);
  box-shadow: 0 0 8px rgba(0,200,150,0.4);
}

.stage-bar.active .stage-fill {
  background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
  animation: pulse-bar 2s ease-in-out infinite;
  box-shadow: 0 0 12px rgba(0,200,150,0.6);
}

.stage-name {
  font-size: 10px;
  color: var(--color-text-muted);
  text-align: center;
  white-space: nowrap;
}

.stage-bar.completed .stage-name,
.stage-bar.active .stage-name {
  color: var(--color-text);
}

.legend {
  display: flex;
  gap: 24px;
  margin-top: 20px;
  justify-content: flex-end;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 13px;
  color: var(--color-text-muted);
}

.legend-dot {
  width: 12px;
  height: 12px;
  border-radius: 3px;
}

.legend-dot.active {
  background: linear-gradient(90deg, var(--color-primary), var(--color-accent));
}

.legend-dot.completed {
  background: var(--color-primary);
}

.legend-dot.pending {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
}

@keyframes pulse-bar {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.7; }
}

@media (max-width: 900px) {
  .pipeline-header,
  .pipeline-row {
    grid-template-columns: 1fr;
    gap: 12px;
  }

  .pipeline-header {
    display: none;
  }

  .ph-stages, .pd-stages {
    display: none;
  }
}
</style>
