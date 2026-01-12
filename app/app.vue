<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const currentSlide = ref(0);
const slides = [
  "/images/slide1.jpg",
  "/images/slide2.png",
  "/images/slide3.png",
];

const facts = [
  {
    text: "Cari tahu sama-sama informasi seputar vaksin",
    image: "/images/card-1.jpg",
    targetId: "detail-info",
  },
  {
    text: "Belajar sama-sama lewat fakta yang ada biar ga salah arah",
    image: "/images/card-2.png",
    targetId: "detail-fakta",
  },
  {
    text: "Sama-sama juga saling dukung dengan tetap jalanin protokol 3M",
    image: "/images/card-3.png",
    targetId: "detail-protokol",
  },
];

const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  }
};

useHead({
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/images/logo.png",
    },
  ],
  title: "Vaksin Untuk Kita",
});

let intervalId;

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
};

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length;
};

onMounted(() => {
  intervalId = setInterval(nextSlide, 5000);
  
  // Scroll Reveal Logic
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
});

const locations = [
  {
    name: "RSUD Cengkareng",
    address: "Jl. Kamal Raya, Cengkareng Tim., Kecamatan Cengkareng, Kota Jakarta Barat",
    type: "Rumah Sakit",
    status: "Tersedia"
  },
  {
    name: "Puskesmas Kecamatan Gambir",
    address: "Jl. Tanah Abang I No.10, Petojo Sel., Kecamatan Gambir, Kota Jakarta Pusat",
    type: "Puskesmas",
    status: "Terbatas"
  },
  {
    name: "Mall Grand Indonesia",
    address: "Jl. M.H. Thamrin No.1, Menteng, Kec. Menteng, Kota Jakarta Pusat",
    type: "Sentra Vaksinasi",
    status: "Tersedia"
  }
];


onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
});
</script>

<template>
  <div class="container">
    <header>
      <nav>
        <div class="logo">
          <img src="/images/logo.png" alt="Vaksin Untuk Kita" />
        </div>
      </nav>
    </header>

    <main>
      <!-- Section 1: Carousel -->
      <section class="section-carousel">
        <div class="carousel">
          <div
            class="carousel-inner"
            :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
          >
            <div
              v-for="(slide, index) in slides"
              :key="index"
              class="carousel-item"
            >
              <img :src="slide" :alt="'Slide ' + (index + 1)" />
            </div>
          </div>

          <button class="carousel-control prev" @click="prevSlide">
            &#10094;
          </button>
          <button class="carousel-control next" @click="nextSlide">
            &#10095;
          </button>

          <div class="carousel-indicators">
            <span
              v-for="(_, index) in slides"
              :key="index"
              :class="{ active: currentSlide === index }"
              @click="currentSlide = index"
            ></span>
          </div>
        </div>
      </section>

      <!-- Section 2: Information -->
      <section class="section-info">
        <div class="content-wrapper">
          <div class="slogan-container">
            <h1 class="slogan">Tempat buat kita saling kasih semangat</h1>
          </div>

          <div class="facts-container">
            <ul class="facts-list">
              <li
                v-for="(fact, index) in facts"
                :key="index"
                class="fact-card"
                :style="{ backgroundImage: `url(${fact.image})` }"
                @click="scrollToSection(fact.targetId)"
              >
                <div class="fact-overlay">
                  <span class="text">{{ fact.text }}</span>
                </div>
              </li>
            </ul>
            <div class="small-tag">#VaksinUntukKita</div>
          </div>
        </div>
      </section>

      <!-- Detailed Sections -->
      <section id="detail-info" class="section-detail section-light">
        <div class="container-narrow">
          <h2>Informasi Seputar Vaksin</h2>
          <p class="lead">
            Vaksinasi adalah cara paling efektif untuk melindungi diri, keluarga, dan masyarakat dari penyebaran COVID-19.
          </p>
          <div class="detail-grid">
            <div class="detail-item">
              <h3>Kenapa Perlu Vaksin?</h3>
              <p>Membentuk kekebalan kelompok (herd immunity) dan menurunkan angka kesakitan serta kematian.</p>
            </div>
            <div class="detail-item">
              <h3>Jenis Vaksin</h3>
              <p>Sinovac, AstraZeneca, Moderna, Pfizer, dan jenis lainnya yang telah disetujui BPOM aman digunakan.</p>
            </div>
          </div>
        </div>
      </section>

      <section id="detail-fakta" class="section-detail section-dark">
        <div class="container-narrow">
          <h2>Fakta vs Hoaks</h2>
          <p class="lead">Jangan mudah percaya berita yang tidak jelas sumbernya. Cek faktanya dulu.</p>
          <div class="detail-grid">
            <div class="detail-item">
              <h3>Hoaks: Vaksin Mengandung Chip</h3>
              <p><strong>Fakta:</strong> Tidak ada microchip dalam vaksin. Vaksin murni berisi bahan medis untuk kekebalan tubuh.</p>
            </div>
            <div class="detail-item">
              <h3>Hoaks: Vaksin Membuat Mandul</h3>
              <p><strong>Fakta:</strong> Tidak ada bukti ilmiah yang mengaitkan vaksin COVID-19 dengan gangguan kesuburan.</p>
            </div>
          </div>
        </div>
      </section>

      <section id="detail-protokol" class="section-detail section-light">
        <div class="container-narrow">
          <h2>Protokol 3M</h2>
          <p class="lead">Vaksinasi penting, tapi protokol kesehatan tetap wajib dijalankan.</p>
          <div class="protocol-list">
            <div class="protocol-item">
              <div class="icon-circle">
                <!-- Medical Mask Icon -->
                <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M21.5 13.5v-1a2 2 0 0 0-2-2h-3v-1a2 2 0 0 0-2-2h-5a2 2 0 0 0-2 2v1h-3a2 2 0 0 0-2 2v1"></path>
                  <path d="M2.5 13.5h19"></path>
                  <path d="M5.5 13.5v4a2 2 0 0 0 2 2h9a2 2 0 0 0 2-2v-4"></path>
                  <path d="M12 7.5v-2"></path>
                </svg>
              </div>
              <h3>Memakai Masker</h3>
              <p>Gunakan masker medis atau kain lapis tiga saat beraktivitas di luar rumah.</p>
            </div>
          </div>
          
          <div class="protocol-list">
            <div class="protocol-item">
               <div class="icon-circle">
                 <!-- Mask Icon -->
                 <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                   <path d="M9 12h6"></path>
                   <path d="M12 3a7 7 0 0 0-7 7v3a4 4 0 0 0 4 4h6a4 4 0 0 0 4-4v-3a7 7 0 0 0-7-7z"></path>
                   <path d="M12 12v3"></path>
                 </svg>
               </div>
              <h3>Memakai Masker</h3>
              <p>Gunakan masker medis atau kain lapis tiga saat beraktivitas di luar rumah.</p>
            </div>
            <div class="protocol-item">
              <div class="icon-circle">
                <!-- Washing Hands (Droplet/Hand) -->
                <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                  <path d="M12 22a7 7 0 0 0 7-7c0-2-1-3.9-3-5.5s-3.5-4-4-6.5c-.5 2.5-2 4.9-4 6.5C6 11.1 5 13 5 15a7 7 0 0 0 7 7z"></path>
                </svg>
              </div>
              <h3>Mencuci Tangan</h3>
              <p>Cuci tangan dengan sabun dan air mengalir selama minimal 20 detik.</p>
            </div>
            <div class="protocol-item">
               <div class="icon-circle">
                 <!-- Social Distancing (User arrows) -->
                 <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                   <circle cx="17" cy="7" r="4"></circle>
                   <path d="M17 11v2h-2"></path>
                   <circle cx="7" cy="17" r="4"></circle>
                   <path d="M7 21v-2h2"></path>
                   <line x1="7" y1="7" x2="17" y2="17"></line>
                 </svg>
               </div>
              <h3>Menjaga Jarak</h3>
              <p>Hindari kerumunan dan jaga jarak minimal 1-2 meter dari orang lain.</p>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="site-footer">
      <div class="footer-container">
        <div class="footer-col">
          <div class="footer-logo">
            <img src="/images/logo.png" alt="Vaksin Untuk Kita Logo" />
          </div>
          <p>Membantu masyarakat Indonesia mendapatkan informasi terpercaya tentang vaksinasi COVID-19.</p>
        </div>
        <div class="footer-col">
          <h4>Tautan Cepat</h4>
          <ul>
            <li @click="scrollToSection('detail-info')">Informasi Vaksin</li>
            <li @click="scrollToSection('detail-fakta')">Fakta & Hoaks</li>
            <li @click="scrollToSection('detail-protokol')">Protokol 3M</li>
          </ul>
        </div>
        <div class="footer-col">
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
  </div>
</template>

<style>
/* Global Styles */
@import url("https://fonts.googleapis.com/css2?family=Outfit:wght@400;700&display=swap");

:root {
  --primary-red: #ee1c25;
  --primary-white: #ffffff;
  --text-dark: #333333;
}

body {
  margin: 0;
  padding: 0;
  font-family: "Outfit", sans-serif;
  box-sizing: border-box;
  background-color: var(--primary-white);
  color: var(--text-dark);
}

.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  background-color: var(--primary-red);
  color: var(--primary-white);
  padding: 1rem 2rem;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}

.logo img {
  height: 40px;
  width: auto;
  display: block;
}

main {
  flex: 1;
}

/* Section 1: Carousel */
.section-carousel {
  position: relative;
  overflow: hidden;
  height: calc(
    100vh - 80px
  ); /* Fill remaining viewport height (approx 80px header) */
  background-color: #f0f0f0;
}

.carousel {
  position: relative;
  width: 100%;
  height: 100%;
}

.carousel-inner {
  display: flex;
  transition: transform 0.5s ease-in-out;
}

.carousel-item {
  min-width: 100%;
  height: 100%;
}

.carousel-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
}

.carousel-control {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(238, 28, 37, 0.7); /* Red with opacity */
  color: white;
  border: none;
  font-size: 2rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.carousel-control:hover {
  background-color: rgba(238, 28, 37, 1);
}

.carousel-control.prev {
  left: 0;
  border-radius: 0 5px 5px 0;
}
.carousel-control.next {
  right: 0;
  border-radius: 5px 0 0 5px;
}

.carousel-indicators {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
}

.carousel-indicators span {
  width: 12px;
  height: 12px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  cursor: pointer;
  transition: background-color 0.3s;
}

.carousel-indicators span.active {
  background-color: var(--primary-red);
  border: 2px solid white;
}

/* Section 2: Info */
.section-info {
  padding: 5rem 2rem;
  background: linear-gradient(180deg, var(--primary-white) 0%, #fff5f5 100%);
  display: flex;
  justify-content: center;
  align-items: center;
}

.content-wrapper {
  max-width: 1000px;
  width: 100%;
  text-align: center;
}

.slogan {
  font-size: 3rem;
  color: var(--primary-red);
  margin-bottom: 4rem;
  font-weight: 800;
  line-height: 1.2;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.facts-container {
  margin-bottom: 3rem;
}

.facts-list {
  list-style: none;
  padding: 0;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

/* Fact Card with Image Background */
.fact-card {
  height: 400px; /* Fixed height for consistency */
  border-radius: 16px;
  background-size: cover;
  background-position: center;
  position: relative;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  list-style: none; /* Remove list bullet */
  padding: 0; /* Reset padding */
  border: none; /* Reset border */
}

.fact-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(238, 28, 37, 0.25);
}

.fact-overlay {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 2rem 1.5rem 1.5rem;
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.9) 0%,
    rgba(0, 0, 0, 0.6) 60%,
    transparent 100%
  );
  display: flex;
  align-items: flex-end;
  box-sizing: border-box;
}

.text {
  font-size: 1.3rem;
  font-weight: 700;
  line-height: 1.4;
  color: white;
  text-align: left;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
  margin: 0;
}

.small-tag {
  margin-top: 4rem;
  display: inline-block;
  font-weight: 800;
  font-size: 1.5rem;
  color: var(--primary-white);
  background-color: var(--primary-red);
  padding: 0.5rem 2rem;
  border-radius: 50px;
  box-shadow: 0 10px 20px rgba(238, 28, 37, 0.3);
  letter-spacing: 1px;
}

footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 1rem;
  margin-top: auto;
}

/* Detail Sections */
.section-detail {
  padding: 6rem 2rem;
}

.section-light {
  background-color: var(--primary-white);
}

.section-dark {
  background-color: #f9f9f9;
}

.container-narrow {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.section-detail h2 {
  font-size: 2.5rem;
  color: var(--primary-red);
  margin-bottom: 1.5rem;
  font-weight: 700;
}

.section-detail .lead {
  font-size: 1.25rem;
  color: #555;
  margin-bottom: 3rem;
  line-height: 1.6;
}

.detail-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  text-align: left;
}

.detail-item {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
}

.section-dark .detail-item {
  background: white; /* Keep cards white on grey bg */
}

.detail-item h3 {
  color: var(--primary-red);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.protocol-list {
  display: flex;
  justify-content: center;
  gap: 3rem;
  flex-wrap: wrap;
}

.protocol-item {
  flex: 1;
  min-width: 250px;
}

.protocol-item .icon-circle {
  width: 80px;
  height: 80px;
  background-color: #fff5f5;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  transition: transform 0.3s ease, background-color 0.3s ease;
}

.protocol-item:hover .icon-circle {
  transform: scale(1.1);
  background-color: #ffe0e0;
}

.protocol-icon {
  width: 40px;
  height: 40px;
  stroke: var(--primary-red);
}

.protocol-item h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--primary-red);
}

/* Responsive */
@media (max-width: 768px) {
  .slogan {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .section-detail {
    padding: 3rem 1.5rem;
  }

  .facts-list,
  .detail-grid,
  .footer-container {
    grid-template-columns: 1fr; /* Force single column */
  }

  .fact-card {
    height: 300px;
  }

  .text {
    font-size: 1.1rem;
  }
  
  .carousel-control {
    padding: 0.5rem;
    font-size: 1.5rem;
  }
}

/* Animations */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Location Card Styles */
.location-card {
  display: flex;
  flex-direction: column;
}

.location-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.location-header h3 {
  margin: 0;
  font-size: 1.25rem;
}

.status-badge {
  font-size: 0.8rem;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-weight: 700;
}

.status-badge.success {
  background-color: #e6fffa;
  color: #047857;
}

.status-badge.warning {
  background-color: #fffaf0;
  color: #c05621;
}

.location-address {
  color: #666;
  font-size: 0.95rem;
  margin-bottom: 0.5rem;
  flex-grow: 1;
}

.location-type {
  font-size: 0.85rem;
  color: #888;
  font-weight: 600;
  text-transform: uppercase;
  margin: 0;
  margin-top: auto;
}

/* Footer Styles */
.site-footer {
  background-color: #1a1a1a;
  color: #e0e0e0;
  padding: 4rem 2rem 1rem;
}

.footer-container {
  max-width: 1000px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 3rem;
  margin-bottom: 3rem;
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
</style>
