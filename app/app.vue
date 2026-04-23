<script setup>
const router = useRouter();

const scrollToSection = (id) => {
  const element = document.getElementById(id);
  if (element) {
    element.scrollIntoView({ behavior: "smooth" });
  } else {
    router.push({ path: '/', hash: '#' + id });
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
</script>

<template>
  <div class="container">
    <LayoutAppHeader />

    <main>
      <NuxtPage />
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
