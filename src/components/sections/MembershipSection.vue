<template>
  <section
    id="membership"
    class="membership"
  >

    <div class="container">

      <span class="section-eyebrow">
        Абонементи
      </span>

      <h2 class="section-title">
        Обери свій рівень
      </h2>

      <p class="membership__subtitle">
        Гнучкі тарифи для будь-якої цілі —
        від перших тренувань до професійного рівня.
      </p>

      <div class="pricing-grid">

        <article
          v-for="plan in memberships"
          :key="plan.id"
          class="pricing-card"
          :class="{ 'pricing-card--featured': plan.featured }"
        >

          <div v-if="plan.featured" class="popular-badge">
            Найпопулярніший
          </div>

          <div class="pricing-card__top">

            <h3>{{ plan.name }}</h3>

            <p>{{ plan.tagline }}</p>

          </div>

          <div class="price">
            {{ plan.price }}
            <span>грн / міс</span>
          </div>

          <ul class="features">
            <li v-for="feature in plan.features" :key="feature">{{ feature }}</li>
          </ul>

          <button class="pricing-btn" @click="selectPlan(plan)">
            Обрати тариф
          </button>

        </article>

      </div>

    </div>

  </section>
</template>

<script setup>
import memberships from '@/data/memberships'

function selectPlan(plan) {
  const contactSection = document.querySelector('#contact')
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: 'smooth' })
  }
  window.dispatchEvent(new CustomEvent('plan-selected', { detail: plan.name }))
}
</script>

<style scoped>

.membership {
  padding: 120px 0;
}

.membership__subtitle {
  max-width: 720px;
  margin-top: 18px;
  color: var(--muted);
  line-height: 1.8;
}

.pricing-grid {

  margin-top: 60px;

  display: grid;

  grid-template-columns:
    repeat(3,1fr);

  gap: 28px;
}

.pricing-card {

  position: relative;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);

  border-radius: 30px;

  padding: 40px 32px;

  transition:
    transform .35s ease,
    border-color .35s ease,
    box-shadow .35s ease;
}

.pricing-card:hover {

  transform: translateY(-10px);

  border-color:
    rgba(212,175,55,.35);

  box-shadow:
    0 30px 60px rgba(0,0,0,.25);
}

.pricing-card--featured {

  border:
    2px solid var(--gold);

  transform: scale(1.03);
}

.pricing-card--featured:hover {
  transform:
    scale(1.03)
    translateY(-10px);
}

.popular-badge {

  position: absolute;

  top: 18px;
  right: 18px;

  background: var(--gold);

  color: black;

  font-size: .8rem;

  font-weight: 700;

  padding: 8px 14px;

  border-radius: 999px;
}

.pricing-card__top h3 {

  font-size: 1.8rem;

  margin-bottom: 6px;
}

.pricing-card__top p {
  color: var(--muted);
}

.price {

  margin: 30px 0;

  font-size: 3rem;

  font-weight: 900;

  color: var(--gold);
}

.price span {

  display: block;

  font-size: .95rem;

  color: var(--muted);

  margin-top: 8px;
}

.features {

  list-style: none;

  padding: 0;

  margin: 0;
}

.features li {

  padding: 14px 0;

  border-bottom:
    1px solid rgba(255,255,255,.06);

  color: var(--muted);
}

.features li:last-child {
  border-bottom: none;
}

.pricing-btn {

  width: 100%;

  margin-top: 30px;

  border: none;

  cursor: pointer;

  padding: 16px;

  border-radius: 16px;

  background: var(--gold);

  color: black;

  font-weight: 800;

  transition: .3s ease;
}

.pricing-btn:hover {

  transform: translateY(-2px);

  opacity: .9;
}

@media(max-width:1100px){

  .pricing-grid{
    grid-template-columns:
      repeat(2,1fr);
  }
}

@media(max-width:768px){

  .membership{
    padding:90px 0;
  }

  .pricing-grid{
    grid-template-columns:1fr;
  }

  .pricing-card--featured{
    transform:none;
  }

  .pricing-card--featured:hover{
    transform:translateY(-10px);
  }

  .price{
    font-size:2.5rem;
  }
}
</style>