<template>
  <header class="site-header">
    <nav>
      <div class="logo">
        <img src="/images/logo.png" alt="Vaksin Untuk Kita" />
      </div>
    </nav>
  </header>
</template>

<style scoped>
.site-header {
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
</style>
