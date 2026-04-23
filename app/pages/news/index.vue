<script setup>
const router = useRouter();

useHead({
  title: "Berita & Artikel - Vaksin Untuk Kita",
});

const allNews = [
  {
    id: 1,
    title: "Vaksin Booster Tersedia di Berbagai Fasilitas Kesehatan",
    date: "10 Okt 2026",
    summary: "Pemerintah memperluas akses vaksin booster untuk masyarakat umum di berbagai faskes. Vaksinasi booster kini lebih mudah diakses di puskesmas, klinik, dan sentra vaksinasi terdekat.",
    image: "https://images.pexels.com/photos/5878500/pexels-photo-5878500.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 2,
    title: "Pentingnya Menjaga Protokol Kesehatan Usai Vaksinasi",
    date: "05 Okt 2026",
    summary: "Meski sudah divaksinasi, protokol kesehatan 3M tetap penting untuk mencegah penularan. Pelajari bagaimana menjaga diri sendiri dan orang lain dengan menerapkan 3M secara konsisten.",
    image: "https://images.pexels.com/photos/5994803/pexels-photo-5994803.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 3,
    title: "Mitos vs Fakta Seputar Efek Samping Vaksin",
    date: "01 Okt 2026",
    summary: "Ketahui fakta sebenarnya tentang efek samping vaksin agar tidak termakan hoaks. Jangan biarkan informasi yang salah menghalangi Anda untuk mendapatkan perlindungan dari vaksin.",
    image: "https://images.pexels.com/photos/8770712/pexels-photo-8770712.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 4,
    title: "Program Vaksinasi Anak Usia 6-11 Tahun Berjalan Lancar",
    date: "28 Sep 2026",
    summary: "Antusiasme masyarakat tinggi dalam mengikuti program vaksinasi untuk anak-anak, mendorong percepatan pemulihan kegiatan belajar mengajar tatap muka.",
    image: "https://images.pexels.com/photos/5994793/pexels-photo-5994793.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 5,
    title: "Pusat Riset Kembangkan Vaksin Varian Baru",
    date: "20 Sep 2026",
    summary: "Ilmuwan terus bekerja keras mengembangkan vaksin yang efektif melawan berbagai varian baru virus yang bermunculan di seluruh dunia.",
    image: "https://images.pexels.com/photos/5863302/pexels-photo-5863302.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 6,
    title: "Cara Mendaftar Vaksinasi Lewat Aplikasi",
    date: "15 Sep 2026",
    summary: "Panduan lengkap cara mendaftar jadwal vaksinasi COVID-19 melalui aplikasi resmi pemerintah dengan cepat dan mudah tanpa harus antre lama.",
    image: "https://images.pexels.com/photos/5995049/pexels-photo-5995049.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 7,
    title: "Update Aturan Perjalanan Selama Masa Vaksinasi",
    date: "10 Sep 2026",
    summary: "Simak aturan terbaru mengenai syarat perjalanan darat, laut, dan udara yang wajib diketahui masyarakat.",
    image: "https://images.pexels.com/photos/5994793/pexels-photo-5994793.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 8,
    title: "Layanan Telemedisin Gratis Bagi Pasien Isoman",
    date: "05 Sep 2026",
    summary: "Kementerian Kesehatan bekerja sama dengan berbagai platform untuk menyediakan layanan konsultasi medis dan obat gratis.",
    image: "https://images.pexels.com/photos/5878500/pexels-photo-5878500.jpeg?auto=compress&cs=tinysrgb&w=800"
  },
  {
    id: 9,
    title: "Kenali Gejala Ringan Usai Vaksin dan Penanganannya",
    date: "01 Sep 2026",
    summary: "Gejala seperti demam ringan dan pegal adalah respons alami tubuh. Pelajari cara penanganan yang tepat di rumah.",
    image: "https://images.pexels.com/photos/5994803/pexels-photo-5994803.jpeg?auto=compress&cs=tinysrgb&w=800"
  }
];

const currentPage = ref(1);
const itemsPerPage = 6;

const totalPages = computed(() => Math.ceil(allNews.length / itemsPerPage));

const paginatedNews = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  const end = start + itemsPerPage;
  return allNews.slice(start, end);
});

const goToPage = (page) => {
  if (page >= 1 && page <= totalPages.value) {
    currentPage.value = page;
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
};

const goToNewsDetail = (id) => {
  router.push(`/news/${id}`);
};

const goBack = () => {
  router.push('/');
};
</script>

<template>
  <div class="news-page">
    <div class="page-header">
      <div class="header-content">
        <h1>Berita & Artikel</h1>
        <p>Kumpulan berita, artikel, dan informasi terbaru seputar vaksinasi dan kesehatan masyarakat.</p>
      </div>
    </div>

    <div class="news-container">
      <div class="breadcrumb">
        <span @click="goBack" class="breadcrumb-link">Beranda</span> &gt; <span>Berita</span>
      </div>

      <div class="news-grid">
        <div v-for="item in paginatedNews" :key="item.id" class="news-card" @click="goToNewsDetail(item.id)">
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
      
      <div class="pagination" v-if="totalPages > 1">
        <button class="page-btn" :disabled="currentPage === 1" @click="goToPage(currentPage - 1)">&larr; Sebelumnya</button>
        <button 
          v-for="page in totalPages" 
          :key="page" 
          class="page-btn" 
          :class="{ active: currentPage === page }"
          @click="goToPage(page)"
        >
          {{ page }}
        </button>
        <button class="page-btn" :disabled="currentPage === totalPages" @click="goToPage(currentPage + 1)">Selanjutnya &rarr;</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.news-page {
  background-color: #f9fafb;
  min-height: calc(100vh - 150px);
  padding-bottom: 5rem;
}

.page-header {
  background-color: var(--primary-red);
  color: white;
  padding: 4rem 1.5rem;
  text-align: center;
}

.header-content {
  max-width: 800px;
  margin: 0 auto;
}

.header-content h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.header-content p {
  font-size: 1.2rem;
  opacity: 0.9;
}

.news-container {
  max-width: 1200px;
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

.news-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
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
  height: 220px;
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

.pagination {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
}

.page-btn {
  padding: 0.5rem 1rem;
  border: 1px solid #ddd;
  background: white;
  border-radius: 6px;
  cursor: pointer;
  color: #333;
  transition: all 0.2s;
}

.page-btn:hover:not(:disabled) {
  background: #f1f1f1;
}

.page-btn.active {
  background: var(--primary-red);
  color: white;
  border-color: var(--primary-red);
}

.page-btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .page-header {
    padding: 3rem 1rem;
  }
  
  .header-content h1 {
    font-size: 2rem;
  }
}
</style>
