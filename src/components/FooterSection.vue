<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-top">
        <div class="footer-brand">
          <a href="#" class="logo">
            <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
              <circle cx="14" cy="14" r="13" stroke="#00C896" stroke-width="2"/>
              <path d="M8 14c0-3.31 2.69-6 6-6s6 2.69 6 6-2.69 6-6 6" stroke="#00C896" stroke-width="2" stroke-linecap="round"/>
              <circle cx="14" cy="14" r="3" fill="#00C896"/>
            </svg>
            <span class="logo-text">BioNova</span>
          </a>
          <p class="brand-desc">
            以科學創新為驅動力，<br />
            致力於改善人類健康，<br />
            打造更美好的生命未來。
          </p>
          <div class="certifications">
            <span v-for="cert in certs" :key="cert" class="cert-badge">{{ cert }}</span>
          </div>
        </div>

        <div v-for="col in footerLinks" :key="col.title" class="footer-col">
          <h4 class="footer-col-title">{{ col.title }}</h4>
          <ul>
            <li v-for="link in col.links" :key="link">
              <a href="#">{{ link }}</a>
            </li>
          </ul>
        </div>
      </div>

      <div class="footer-bottom">
        <p class="copyright">
          &copy; 2026 BioNova Biotechnology Co., Ltd. All rights reserved.
        </p>
        <div class="footer-legal">
          <a href="#">隱私政策</a>
          <a href="#">使用條款</a>
          <a href="#">法律聲明</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const certs = ['ISO 9001', 'GMP 認證', 'FDA 登記', 'EMA 認可']

const footerLinks = [
  {
    title: '研究與開發',
    links: ['研究領域', '產品管線', '臨床試驗', '技術平台', '科學出版'],
  },
  {
    title: '公司資訊',
    links: ['關於我們', '管理團隊', '企業治理', '永續發展', '投資者關係'],
  },
  {
    title: '資源中心',
    links: ['新聞稿', '科學部落格', '年度報告', '媒體資源', '人才招募'],
  },
]
</script>

<style scoped>
.footer {
  background: rgba(5, 10, 20, 0.95);
  border-top: 1px solid var(--color-border);
  padding: 64px 0 32px;
}

.footer-top {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1fr;
  gap: 48px;
  margin-bottom: 48px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 20px;
}

.logo-text {
  font-size: 1.4rem;
  font-weight: 800;
  background: linear-gradient(135deg, #fff, var(--color-primary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.brand-desc {
  font-size: 14px;
  color: var(--color-text-muted);
  line-height: 1.8;
  margin-bottom: 20px;
}

.certifications {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.cert-badge {
  font-size: 11px;
  padding: 4px 10px;
  background: rgba(0, 200, 150, 0.08);
  border: 1px solid rgba(0, 200, 150, 0.2);
  border-radius: 6px;
  color: var(--color-text-muted);
}

.footer-col-title {
  font-size: 13px;
  font-weight: 700;
  color: var(--color-text);
  margin-bottom: 20px;
  letter-spacing: 0.5px;
}

.footer-col ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.footer-col a {
  font-size: 14px;
  color: var(--color-text-muted);
  transition: color var(--transition);
}

.footer-col a:hover {
  color: var(--color-primary);
}

.footer-bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-top: 32px;
  border-top: 1px solid rgba(255,255,255,0.06);
  gap: 24px;
}

.copyright {
  font-size: 13px;
  color: var(--color-text-muted);
}

.footer-legal {
  display: flex;
  gap: 24px;
}

.footer-legal a {
  font-size: 13px;
  color: var(--color-text-muted);
  transition: color var(--transition);
}

.footer-legal a:hover {
  color: var(--color-primary);
}

@media (max-width: 900px) {
  .footer-top {
    grid-template-columns: 1fr 1fr;
  }

  .footer-brand {
    grid-column: span 2;
  }

  .footer-bottom {
    flex-direction: column;
    text-align: center;
  }
}

@media (max-width: 480px) {
  .footer-top {
    grid-template-columns: 1fr;
  }

  .footer-brand {
    grid-column: span 1;
  }
}
</style>
