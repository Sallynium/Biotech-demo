<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="container nav-inner">
      <a href="#" class="logo">
        <span class="logo-icon">
          <svg width="28" height="28" viewBox="0 0 28 28" fill="none">
            <circle cx="14" cy="14" r="13" stroke="#00C896" stroke-width="2"/>
            <path d="M8 14c0-3.31 2.69-6 6-6s6 2.69 6 6-2.69 6-6 6" stroke="#00C896" stroke-width="2" stroke-linecap="round"/>
            <circle cx="14" cy="14" r="3" fill="#00C896"/>
          </svg>
        </span>
        <span class="logo-text">BioNova</span>
      </a>

      <ul class="nav-links" :class="{ open: menuOpen }">
        <li v-for="link in links" :key="link.href">
          <a :href="link.href" @click="menuOpen = false">{{ link.label }}</a>
        </li>
      </ul>

      <div class="nav-actions">
        <a href="#contact" class="btn btn-primary nav-cta">聯絡我們</a>
        <button class="hamburger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
          <span></span><span></span><span></span>
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { href: '#about', label: '關於我們' },
  { href: '#research', label: '研究領域' },
  { href: '#products', label: '產品管線' },
  { href: '#team', label: '團隊' },
  { href: '#news', label: '最新消息' },
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  padding: 20px 0;
  transition: all 0.4s ease;
}

.navbar.scrolled {
  background: rgba(5, 13, 26, 0.92);
  backdrop-filter: blur(20px);
  padding: 12px 0;
  border-bottom: 1px solid var(--color-border);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.4);
}

.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 32px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.logo-text {
  font-size: 1.4rem;
  font-weight: 800;
  background: linear-gradient(135deg, #fff, var(--color-primary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-links {
  display: flex;
  list-style: none;
  gap: 8px;
}

.nav-links a {
  padding: 8px 16px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 500;
  color: var(--color-text-muted);
  transition: all var(--transition);
}

.nav-links a:hover {
  color: var(--color-text);
  background: rgba(255,255,255,0.06);
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}

.nav-cta {
  padding: 10px 22px;
  font-size: 14px;
}

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.hamburger span {
  display: block;
  width: 22px;
  height: 2px;
  background: var(--color-text);
  border-radius: 2px;
  transition: all var(--transition);
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    flex-direction: column;
    background: rgba(5, 13, 26, 0.97);
    backdrop-filter: blur(20px);
    padding: 20px 24px;
    border-bottom: 1px solid var(--color-border);
    gap: 4px;
  }

  .nav-links.open {
    display: flex;
  }

  .hamburger {
    display: flex;
  }

  .nav-cta {
    display: none;
  }
}
</style>
