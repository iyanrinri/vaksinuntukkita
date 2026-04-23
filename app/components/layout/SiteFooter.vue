<script setup>
const emit = defineEmits(["navigate"]);
</script>

<template>
  <footer class="site-footer reveal">
    <div class="footer-container">
      <div class="footer-col reveal">
        <div class="footer-logo">
          <img src="/images/logo.png" alt="Vaksin Untuk Kita Logo" />
        </div>
        <p>Membantu masyarakat Indonesia mendapatkan informasi terpercaya tentang vaksinasi COVID-19.</p>
      </div>
      <div class="footer-col reveal">
        <h4>Tautan Cepat</h4>
        <ul>
          <li @click="emit('navigate', 'detail-info')">Informasi Vaksin</li>
          <li @click="emit('navigate', 'detail-fakta')">Fakta & Hoaks</li>
          <li @click="emit('navigate', 'detail-protokol')">Protokol 3M</li>
        </ul>
      </div>
      <div class="footer-col reveal">
        <h4>Hubungi Kami</h4>
        <div class="social-links">
          <a href="https://www.instagram.com/vaksinuntukkita/" target="_blank" rel="noopener noreferrer" class="social-link">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-instagram"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
            <span>@vaksinuntukkita</span>
          </a>
          <a href="https://www.facebook.com/vaksinuntukkita/?locale=id_ID" target="_blank" rel="noopener noreferrer" class="social-link">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-facebook"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg>
            <span>Vaksin Untuk Kita</span>
          </a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; 2026 Vaksin Untuk Kita. Bangkit Bersama.</p>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background-color: #1a1a1a;
  color: #e0e0e0;
  padding: 3.2rem 1.5rem 1rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.4rem;
  margin-bottom: 2rem;
}

.footer-logo img {
  height: 30px;
  margin-bottom: 1rem;
}

.footer-col h4 {
  color: white;
  margin-bottom: 1.5rem;
  font-size: 1.2rem;
}

.footer-col {
  transition: transform 0.25s ease;
}

.footer-col:hover {
  transform: translateY(-4px);
}

.footer-col ul {
  list-style: none;
  padding: 0;
}

.footer-col ul li {
  margin-bottom: 0.8rem;
  cursor: pointer;
  transition: color 0.3s;
}

.footer-col ul li:hover {
  color: var(--primary-red);
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  color: #e0e0e0;
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: var(--primary-red);
}

.social-link svg {
  width: 20px;
  height: 20px;
}

.footer-bottom {
  border-top: 1px solid #333;
  padding-top: 2rem;
  text-align: center;
  font-size: 0.9rem;
  color: #888;
}

@media (max-width: 768px) {
  .footer-container {
    grid-template-columns: 1fr;
  }
}
</style>
