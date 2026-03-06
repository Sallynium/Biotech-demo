<template>
  <section class="section contact-section" id="contact">
    <div class="container">
      <div class="contact-grid">
        <div class="contact-info">
          <div class="section-label">聯絡我們</div>
          <h2 class="section-title">開啟<span class="highlight">合作對話</span></h2>
          <p class="section-desc">
            無論是合作洽詢、投資者關係，或是對我們的研究感興趣，
            我們的團隊隨時準備好與您交流。
          </p>

          <div class="contact-details">
            <div v-for="detail in contactDetails" :key="detail.label" class="contact-detail">
              <div class="detail-icon">{{ detail.icon }}</div>
              <div>
                <div class="detail-label">{{ detail.label }}</div>
                <div class="detail-value">{{ detail.value }}</div>
              </div>
            </div>
          </div>

          <div class="social-links">
            <a v-for="social in socials" :key="social.name" href="#" class="social-btn">
              {{ social.icon }}
            </a>
          </div>
        </div>

        <div class="contact-form-wrap">
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-row">
              <div class="form-group">
                <label>姓名</label>
                <input v-model="form.name" type="text" placeholder="您的全名" required />
              </div>
              <div class="form-group">
                <label>公司</label>
                <input v-model="form.company" type="text" placeholder="公司/機構名稱" />
              </div>
            </div>
            <div class="form-group">
              <label>電子郵件</label>
              <input v-model="form.email" type="email" placeholder="your@email.com" required />
            </div>
            <div class="form-group">
              <label>合作類型</label>
              <select v-model="form.type">
                <option value="">請選擇...</option>
                <option>研究合作</option>
                <option>授權協議</option>
                <option>投資洽詢</option>
                <option>媒體採訪</option>
                <option>人才招募</option>
                <option>其他</option>
              </select>
            </div>
            <div class="form-group">
              <label>訊息內容</label>
              <textarea v-model="form.message" rows="5" placeholder="請描述您的需求或問題..."></textarea>
            </div>
            <button type="submit" class="btn btn-primary submit-btn" :disabled="submitted">
              <span v-if="!submitted">送出訊息</span>
              <span v-else>✓ 已收到您的訊息！</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const submitted = ref(false)
const form = ref({
  name: '',
  company: '',
  email: '',
  type: '',
  message: '',
})

function submitForm() {
  submitted.value = true
  setTimeout(() => {
    submitted.value = false
    form.value = { name: '', company: '', email: '', type: '', message: '' }
  }, 3000)
}

const contactDetails = [
  { icon: '📍', label: '總部地址', value: '台北市南港區研究院路二段 128 號' },
  { icon: '📞', label: '電話', value: '+886 2 2788-8000' },
  { icon: '✉️', label: '電子郵件', value: 'info@bionova-biotech.com' },
  { icon: '🕐', label: '服務時間', value: '週一至週五 09:00 – 18:00' },
]

const socials = [
  { name: 'LinkedIn', icon: '💼' },
  { name: 'Twitter', icon: '🐦' },
  { name: 'YouTube', icon: '▶️' },
  { name: 'ResearchGate', icon: '🔬' },
]
</script>

<style scoped>
.contact-section {
  background: linear-gradient(180deg, var(--color-bg) 0%, rgba(10,79,110,0.15) 100%);
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 80px;
  align-items: start;
}

.contact-details {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin: 40px 0;
}

.contact-detail {
  display: flex;
  gap: 16px;
  align-items: flex-start;
}

.detail-icon {
  font-size: 22px;
  width: 44px;
  height: 44px;
  background: rgba(0, 200, 150, 0.1);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.detail-label {
  font-size: 12px;
  color: var(--color-text-muted);
  margin-bottom: 2px;
}

.detail-value {
  font-size: 14px;
  font-weight: 500;
}

.social-links {
  display: flex;
  gap: 12px;
}

.social-btn {
  width: 44px;
  height: 44px;
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 18px;
  transition: all var(--transition);
}

.social-btn:hover {
  border-color: var(--color-primary);
  transform: translateY(-3px);
  background: rgba(0, 200, 150, 0.1);
}

/* Form */
.contact-form-wrap {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: 40px;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-group label {
  font-size: 13px;
  font-weight: 600;
  color: var(--color-text-muted);
}

.form-group input,
.form-group select,
.form-group textarea {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid var(--color-border);
  border-radius: var(--radius);
  padding: 12px 16px;
  color: var(--color-text);
  font-family: var(--font-sans);
  font-size: 14px;
  transition: border-color var(--transition);
  resize: vertical;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(0, 200, 150, 0.1);
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: rgba(138, 168, 188, 0.5);
}

.form-group select option {
  background: var(--color-bg-card);
}

.submit-btn {
  width: 100%;
  justify-content: center;
  padding: 16px;
  font-size: 16px;
}

.submit-btn:disabled {
  background: linear-gradient(135deg, #00A07A, #006B52);
  cursor: default;
  transform: none;
}

@media (max-width: 900px) {
  .contact-grid {
    grid-template-columns: 1fr;
    gap: 48px;
  }

  .form-row {
    grid-template-columns: 1fr;
  }
}
</style>
