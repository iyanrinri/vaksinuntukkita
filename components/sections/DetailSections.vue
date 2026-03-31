<template>
  <section id="detail-info" class="section-detail section-light reveal">
    <div class="container-narrow reveal">
      <h2>Informasi Seputar Vaksin</h2>
      <p class="lead">
        Vaksinasi adalah cara paling efektif untuk melindungi diri, keluarga, dan masyarakat dari penyebaran COVID-19.
      </p>
      <div class="detail-grid">
        <div class="detail-item reveal">
          <h3>Kenapa Perlu Vaksin?</h3>
          <p>Membentuk kekebalan kelompok (herd immunity) dan menurunkan angka kesakitan serta kematian.</p>
        </div>
        <div class="detail-item reveal">
          <h3>Jenis Vaksin</h3>
          <p>Sinovac, AstraZeneca, Moderna, Pfizer, dan jenis lainnya yang telah disetujui BPOM aman digunakan.</p>
        </div>
      </div>
    </div>
  </section>

  <section id="detail-fakta" class="section-detail section-dark reveal">
    <div class="container-narrow reveal">
      <h2>Fakta vs Hoaks</h2>
      <p class="lead">Jangan mudah percaya berita yang tidak jelas sumbernya. Cek faktanya dulu.</p>
      <div class="detail-grid">
        <div class="detail-item reveal">
          <h3>Hoaks: Vaksin Mengandung Chip</h3>
          <p><strong>Fakta:</strong> Tidak ada microchip dalam vaksin. Vaksin murni berisi bahan medis untuk kekebalan tubuh.</p>
        </div>
        <div class="detail-item reveal">
          <h3>Hoaks: Vaksin Membuat Mandul</h3>
          <p><strong>Fakta:</strong> Tidak ada bukti ilmiah yang mengaitkan vaksin COVID-19 dengan gangguan kesuburan.</p>
        </div>
      </div>
    </div>
  </section>

  <section id="detail-protokol" class="section-detail section-light reveal">
    <div class="container-narrow reveal">
      <h2>Protokol 3M</h2>
      <p class="lead">Vaksinasi penting, tapi protokol kesehatan tetap wajib dijalankan.</p>

      <div class="protocol-grid">
        <div class="protocol-item protocol-main reveal">
          <div class="icon-circle">
            <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M9 12h6"></path>
              <path d="M12 3a7 7 0 0 0-7 7v3a4 4 0 0 0 4 4h6a4 4 0 0 0 4-4v-3a7 7 0 0 0-7-7z"></path>
              <path d="M12 12v3"></path>
            </svg>
          </div>
          <h3>Memakai Masker</h3>
          <p>Gunakan masker medis atau kain lapis tiga saat beraktivitas di luar rumah.</p>
        </div>

        <div class="protocol-item reveal">
          <div class="icon-circle">
            <svg xmlns="http://www.w3.org/2000/svg" class="protocol-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
              <path d="M12 22a7 7 0 0 0 7-7c0-2-1-3.9-3-5.5s-3.5-4-4-6.5c-.5 2.5-2 4.9-4 6.5C6 11.1 5 13 5 15a7 7 0 0 0 7 7z"></path>
            </svg>
          </div>
          <h3>Mencuci Tangan</h3>
          <p>Cuci tangan dengan sabun dan air mengalir selama minimal 20 detik.</p>
        </div>

        <div class="protocol-item reveal">
          <div class="icon-circle">
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
</template>

<style scoped>
.section-detail {
  padding: 5rem 1.5rem;
}

.section-light {
  background-color: var(--primary-white);
}

.section-dark {
  background-color: #f9f9f9;
}

.container-narrow {
  max-width: 1100px;
  margin: 0 auto;
  text-align: center;
}

.section-detail h2 {
  font-size: 2.5rem;
  color: var(--primary-red);
  margin-bottom: 1.5rem;
  font-weight: 700;
  letter-spacing: 0.01em;
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
  gap: 1.2rem;
  text-align: left;
}

.detail-item {
  background: white;
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  border: 1px solid rgba(238, 28, 37, 0.08);
}

.detail-item:hover {
  transform: translateY(-6px);
  box-shadow: 0 14px 28px rgba(0, 0, 0, 0.09);
}

.section-dark .detail-item {
  background: white;
}

.detail-item h3 {
  color: var(--primary-red);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.protocol-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1.2rem;
}

.protocol-main {
  grid-column: 1 / -1;
}

.protocol-item {
  background: #fff;
  border-radius: 14px;
  padding: 1.6rem 1rem;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.06);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.protocol-item:hover {
  transform: translateY(-6px);
  box-shadow: 0 14px 26px rgba(0, 0, 0, 0.1);
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
  font-size: 1.8rem;
  margin-bottom: 0.8rem;
  color: var(--primary-red);
}

.protocol-item p {
  margin: 0;
  font-size: 1.1rem;
  line-height: 1.5;
}

@media (max-width: 768px) {
  .section-detail {
    padding: 3rem 1.5rem;
  }

  .detail-grid,
  .protocol-grid {
    grid-template-columns: 1fr;
  }

  .protocol-main {
    grid-column: auto;
  }
}
</style>
