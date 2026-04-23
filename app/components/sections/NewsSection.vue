<script setup>
const router = useRouter();

const recentNews = [
  {
    id: 1,
    title: "Vaksin Booster Tersedia di Berbagai Fasilitas Kesehatan",
    date: "10 Okt 2026",
    summary: "Pemerintah memperluas akses vaksin booster untuk masyarakat umum di berbagai faskes.",
    image: "https://images.pexels.com/photos/5878500/pexels-photo-5878500.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 2,
    title: "Pentingnya Menjaga Protokol Kesehatan Usai Vaksinasi",
    date: "05 Okt 2026",
    summary: "Meski sudah divaksinasi, protokol kesehatan 3M tetap penting untuk mencegah penularan.",
    image: "https://images.pexels.com/photos/5994803/pexels-photo-5994803.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 3,
    title: "Mitos vs Fakta Seputar Efek Samping Vaksin",
    date: "01 Okt 2026",
    summary: "Ketahui fakta sebenarnya tentang efek samping vaksin agar tidak termakan hoaks.",
    image: "https://images.pexels.com/photos/8770712/pexels-photo-8770712.jpeg?auto=compress&cs=tinysrgb&w=800"
  }
];

const goToNews = () => {
  router.push('/news');
};

const goToNewsDetail = (id) => {
  router.push(`/news/${id}`);
};
</script>

<template>
  <section class="news-section reveal" id="berita">
    <div class="news-container">
      <div class="section-header">
        <h2>Berita & Artikel Terbaru</h2>
        <p>Tetap update dengan informasi terkini seputar vaksin dan kesehatan.</p>
      </div>

      <div class="news-grid">
        <div v-for="item in recentNews" :key="item.id" class="news-card" @click="goToNewsDetail(item.id)">
          <div class="news-image">
            <img :src="item.image" :alt="item.title" />
          </div>
          <div class="news-content">
            <span class="news-date">{{ item.date }}</span>
            <h3 class="news-title">{{ item.title }}</h3>
            <p class="news-summary">{{ item.summary }}</p>
            <div class="read-more">Baca Selengkapnya &rarr;</div>
          </div>
        </div>
      </div>

      <div class="view-all">
        <button class="btn btn-outline" @click="goToNews">Lihat Semua Berita</button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.news-section {
  padding: 5rem 1.5rem;
  background-color: #f9fafb;
}

.news-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 3.5rem;
}

.section-header h2 {
  font-size: 2.2rem;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.section-header p {
  color: #666;
  font-size: 1.1rem;
  max-width: 600px;
  margin: 0 auto;
}

.news-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.news-card {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  display: flex;
  flex-direction: column;
}

.news-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 20px rgba(0, 0, 0, 0.1);
}

.news-image {
  height: 200px;
  overflow: hidden;
}

.news-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.news-card:hover .news-image img {
  transform: scale(1.05);
}

.news-content {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.news-date {
  font-size: 0.85rem;
  color: #888;
  margin-bottom: 0.5rem;
  display: block;
}

.news-title {
  font-size: 1.25rem;
  color: #1a1a1a;
  margin-bottom: 1rem;
  line-height: 1.4;
}

.news-summary {
  color: #666;
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.read-more {
  color: var(--primary-red);
  font-weight: 600;
  font-size: 0.9rem;
  margin-top: auto;
  transition: color 0.3s;
}

.news-card:hover .read-more {
  color: #d00000;
}

.view-all {
  text-align: center;
}

.btn {
  padding: 0.8rem 2rem;
  border-radius: 30px;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s;
}

.btn-outline {
  background: transparent;
  color: var(--primary-red);
  border: 2px solid var(--primary-red);
}

.btn-outline:hover {
  background: var(--primary-red);
  color: white;
}

@media (max-width: 768px) {
  .section-header h2 {
    font-size: 1.8rem;
  }
}
</style>
