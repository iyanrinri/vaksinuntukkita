<script setup>
const route = useRoute();
const router = useRouter();
const newsId = route.params.id;

// Dummy data for demo
const newsItem = {
  id: newsId,
  title: "Vaksin Booster Tersedia di Berbagai Fasilitas Kesehatan",
  date: "10 Okt 2026",
  author: "Kementerian Kesehatan RI",
  image: "https://images.pexels.com/photos/5878500/pexels-photo-5878500.jpeg?auto=compress&cs=tinysrgb&w=1200",
  content: `
    <p>Pemerintah memperluas akses vaksin booster untuk masyarakat umum di berbagai fasilitas kesehatan (faskes). Langkah ini diambil sebagai upaya untuk meningkatkan antibodi masyarakat di tengah munculnya varian baru virus COVID-19.</p>
    <p>Vaksinasi booster kini lebih mudah diakses di puskesmas, klinik, dan sentra vaksinasi terdekat. Masyarakat tidak perlu lagi menunggu terlalu lama untuk mendapatkan jadwal karena ketersediaan dosis yang cukup memadai di seluruh daerah.</p>
    <h3>Syarat Penerima Vaksin Booster</h3>
    <p>Untuk mendapatkan vaksin booster, terdapat beberapa syarat yang harus dipenuhi:</p>
    <ul>
      <li>Berusia 18 tahun ke atas.</li>
      <li>Telah mendapatkan vaksinasi primer dosis lengkap minimal 3 bulan sebelumnya.</li>
      <li>Membawa KTP asli saat datang ke fasilitas kesehatan.</li>
      <li>Dalam kondisi sehat dan tidak sedang sakit berat.</li>
    </ul>
    <p>Menteri Kesehatan mengimbau agar masyarakat segera memanfaatkan fasilitas ini demi melindungi diri, keluarga, dan orang-orang sekitar. "Jangan tunggu sampai angka kasus naik baru mencari vaksin, perlindungan terbaik adalah perlindungan sedini mungkin," ujar Menkes dalam konferensi pers baru-baru ini.</p>
    <p>Pemerintah juga memastikan bahwa semua jenis vaksin yang digunakan untuk booster telah melalui uji klinis yang ketat dan mendapatkan izin penggunaan darurat (EUA) dari BPOM serta rekomendasi dari ITAGI.</p>
  `
};

useHead({
  title: `${newsItem.title} - Vaksin Untuk Kita`,
});

const goBack = () => {
  router.push('/news');
};
</script>

<template>
  <div class="news-detail-page">
    <div class="container">
      <div class="breadcrumb">
        <span @click="router.push('/')" class="breadcrumb-link">Beranda</span> &gt; 
        <span @click="goBack" class="breadcrumb-link">Berita</span> &gt; 
        <span>Detail</span>
      </div>

      <article class="news-article">
        <header class="article-header">
          <h1 class="article-title">{{ newsItem.title }}</h1>
          <div class="article-meta">
            <span class="meta-item">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></svg>
              {{ newsItem.date }}
            </span>
            <span class="meta-item">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>
              {{ newsItem.author }}
            </span>
          </div>
        </header>

        <div class="article-image">
          <img :src="newsItem.image" :alt="newsItem.title" />
        </div>

        <div class="article-content" v-html="newsItem.content"></div>

        <footer class="article-footer">
          <div class="share-section">
            <span>Bagikan artikel ini:</span>
            <div class="share-buttons">
              <button class="share-btn fb"><svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg></button>
              <button class="share-btn tw"><svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path></svg></button>
              <button class="share-btn wa"><svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg></button>
            </div>
          </div>
        </footer>
      </article>
    </div>
  </div>
</template>

<style scoped>
.news-detail-page {
  background-color: #f9fafb;
  min-height: calc(100vh - 150px);
  padding-bottom: 5rem;
}

.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.breadcrumb {
  padding: 2rem 0;
  color: #666;
  font-size: 0.9rem;
}

.breadcrumb-link {
  color: var(--primary-red);
  cursor: pointer;
  font-weight: 500;
}

.breadcrumb-link:hover {
  text-decoration: underline;
}

.news-article {
  background: white;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
  padding: 2.5rem;
  margin-bottom: 3rem;
}

.article-header {
  margin-bottom: 2rem;
}

.article-title {
  font-size: 2.2rem;
  color: #1a1a1a;
  line-height: 1.3;
  margin-bottom: 1rem;
}

.article-meta {
  display: flex;
  gap: 1.5rem;
  color: #666;
  font-size: 0.9rem;
}

.meta-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.article-image {
  margin-bottom: 2.5rem;
  border-radius: 8px;
  overflow: hidden;
}

.article-image img {
  width: 100%;
  max-height: 500px;
  object-fit: cover;
  display: block;
}

.article-content {
  color: #333;
  font-size: 1.1rem;
  line-height: 1.8;
}

.article-content :deep(p) {
  margin-bottom: 1.5rem;
}

.article-content :deep(h3) {
  font-size: 1.5rem;
  color: #1a1a1a;
  margin: 2rem 0 1rem;
}

.article-content :deep(ul) {
  margin-bottom: 1.5rem;
  padding-left: 1.5rem;
}

.article-content :deep(li) {
  margin-bottom: 0.5rem;
}

.article-footer {
  margin-top: 3rem;
  padding-top: 2rem;
  border-top: 1px solid #eee;
}

.share-section {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: #555;
  font-weight: 500;
}

.share-buttons {
  display: flex;
  gap: 0.8rem;
}

.share-btn {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  cursor: pointer;
  transition: transform 0.2s, opacity 0.2s;
}

.share-btn:hover {
  transform: translateY(-2px);
  opacity: 0.9;
}

.share-btn.fb { background-color: #1877f2; }
.share-btn.tw { background-color: #1da1f2; }
.share-btn.wa { background-color: #25d366; }

@media (max-width: 768px) {
  .news-article {
    padding: 1.5rem;
  }
  
  .article-title {
    font-size: 1.8rem;
  }
}
</style>
