<script setup>
const props = defineProps({
  facts: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["navigate"]);
</script>

<template>
  <section class="section-info reveal">
    <div class="content-wrapper reveal">
      <div class="info-header">
        <p class="section-kicker">OUR COMMUNITY</p>
        <h1 class="slogan">Tempat buat kita saling kasih semangat</h1>
        <p class="section-subtitle">
          Dari edukasi vaksin sampai saling dukung jalani hidup sehat, semua ada di satu tempat.
        </p>
      </div>

      <div class="facts-container">
        <ul class="facts-list">
          <li
            v-for="(fact, index) in facts"
            :key="index"
            class="fact-card reveal"
            :style="{ backgroundImage: `url(${fact.image})` }"
            @click="emit('navigate', fact.targetId)"
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
</template>

<style scoped>
.section-info {
  padding: 4.5rem 1.5rem;
  background: linear-gradient(180deg, var(--primary-white) 0%, #fff5f5 100%);
  display: flex;
  justify-content: center;
  align-items: center;
}

.content-wrapper {
  max-width: 1240px;
  width: 100%;
  text-align: left;
}

.info-header {
  margin-bottom: 2rem;
}

.section-kicker {
  margin: 0 0 0.6rem;
  color: #31aef2;
  font-weight: 800;
  letter-spacing: 0.06em;
  font-size: 0.95rem;
}

.section-subtitle {
  margin: 0;
  color: #6d7587;
  font-size: 1.35rem;
  line-height: 1.5;
  max-width: 780px;
}

.slogan {
  font-size: clamp(2rem, 4vw, 4rem);
  color: #09142f;
  margin: 0 0 0.9rem;
  font-weight: 800;
  line-height: 1.08;
  text-shadow: none;
  max-width: 920px;
}

.facts-container {
  margin-bottom: 2rem;
}

.facts-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.1rem;
}

.fact-card {
  height: 345px;
  border-radius: 16px;
  background-size: cover;
  background-position: center;
  position: relative;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  list-style: none;
  padding: 0;
  border: none;
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
  transition: background 0.3s ease;
}

.fact-card:hover .fact-overlay {
  background: linear-gradient(
    to top,
    rgba(0, 0, 0, 0.95) 0%,
    rgba(0, 0, 0, 0.7) 62%,
    transparent 100%
  );
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
  margin-top: 1.25rem;
  display: inline-block;
  font-weight: 800;
  font-size: 1.1rem;
  color: var(--primary-white);
  background-color: var(--primary-red);
  padding: 0.45rem 1.4rem;
  border-radius: 50px;
  box-shadow: 0 10px 20px rgba(238, 28, 37, 0.3);
  letter-spacing: 1px;
}

@media (max-width: 768px) {
  .slogan {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .section-subtitle {
    font-size: 1rem;
  }

  .facts-list {
    grid-template-columns: 1fr;
  }

  .fact-card {
    height: 300px;
  }

  .text {
    font-size: 1.1rem;
  }
}
</style>
