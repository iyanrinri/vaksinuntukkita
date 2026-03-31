<script setup>
import LayoutAppHeader from "~~/components/layout/AppHeader.vue";
import LayoutSiteFooter from "~~/components/layout/SiteFooter.vue";
import SectionsCarouselSection from "~~/components/sections/CarouselSection.vue";
import SectionsCommunitySection from "~~/components/sections/CommunitySection.vue";
import SectionsDetailSections from "~~/components/sections/DetailSections.vue";

let revealObserver;

const slides = [
  {
    image: "https://images.pexels.com/photos/5994793/pexels-photo-5994793.jpeg?auto=compress&cs=tinysrgb&w=1800",
    title: "Akses Informasi Vaksin Lebih Mudah",
    description: "Cari informasi terpercaya seputar vaksin untuk lindungi diri, keluarga, dan orang terdekat.",
    ctaLabel: "Lihat Informasi",
    targetId: "detail-info",
  },
  {
    image: "https://images.pexels.com/photos/5878500/pexels-photo-5878500.jpeg?auto=compress&cs=tinysrgb&w=1800",
    title: "Kenali Fakta, Hindari Hoaks",
    description: "Pahami fakta medis yang benar supaya kamu tidak mudah terpengaruh informasi yang menyesatkan.",
    ctaLabel: "Cek Fakta",
    targetId: "detail-fakta",
  },
  {
    image: "https://images.pexels.com/photos/5995049/pexels-photo-5995049.jpeg?auto=compress&cs=tinysrgb&w=1800",
    title: "Tetap Disiplin Jalankan 3M",
    description: "Vaksinasi dan protokol kesehatan berjalan bersama untuk bantu Indonesia tetap kuat.",
    ctaLabel: "Pelajari 3M",
    targetId: "detail-protokol",
  },
];

const facts = [
  {
    text: "Cari tahu sama-sama informasi seputar vaksin",
    image: "https://images.pexels.com/photos/5863302/pexels-photo-5863302.jpeg?auto=compress&cs=tinysrgb&w=1200",
    targetId: "detail-info",
  },
  {
    text: "Belajar sama-sama lewat fakta yang ada biar ga salah arah",
    image: "https://images.pexels.com/photos/8770712/pexels-photo-8770712.jpeg?auto=compress&cs=tinysrgb&w=1200",
    targetId: "detail-fakta",
  },
  {
    text: "Sama-sama juga saling dukung dengan tetap jalanin protokol 3M",
    image: "https://images.pexels.com/photos/5994803/pexels-photo-5994803.jpeg?auto=compress&cs=tinysrgb&w=1200",
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

onMounted(() => {
  revealObserver = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add("visible");
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll(".reveal").forEach((el) => revealObserver.observe(el));
});

onUnmounted(() => {
  if (revealObserver) revealObserver.disconnect();
});
</script>

<template>
  <div class="container">
    <LayoutAppHeader />

    <main>
      <SectionsCarouselSection :slides="slides" @navigate="scrollToSection" />
      <SectionsCommunitySection :facts="facts" @navigate="scrollToSection" />
      <SectionsDetailSections />
    </main>

    <LayoutSiteFooter @navigate="scrollToSection" />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
