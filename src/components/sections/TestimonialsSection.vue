<template>
  <section
    id="testimonials"
    class="testimonials"
  >
    <div class="container">

      <span class="section-eyebrow">
        Відгуки клієнтів
      </span>

      <h2 class="section-title">
        Результати говорять самі за себе
      </h2>

      <p class="testimonials__subtitle">
        Реальні історії людей,
        які обрали MHP GYM.
      </p>

      <div class="reviews-grid">

        <article
          v-for="review in reviews"
          :key="review.id"
          class="review-card"
        >

          <div class="review-card__header">

            <div class="review-avatar">
              {{ review.initials }}
            </div>

            <div>

              <h3>
                {{ review.name }}
              </h3>

              <span class="review-period">
                {{ review.period }}
              </span>

            </div>

          </div>

          <div class="review-stars">
            ★★★★★
          </div>

          <div class="review-result">
            {{ review.result }}
          </div>

          <p class="review-text">
            {{ review.text }}
          </p>

        </article>

      </div>

    </div>
  </section>
</template>

<script setup>
import reviews from '@/data/reviews'
</script>

<style scoped>

.testimonials {
  padding: 120px 0;
}

.testimonials__subtitle {
  max-width: 700px;
  margin-top: 16px;
  color: var(--muted);
}

.reviews-grid {

  margin-top: 60px;

  display: grid;

  grid-template-columns:
    repeat(3, 1fr);

  gap: 24px;
}

.review-card {

  padding: 30px;

  border-radius: 28px;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);

  transition:
    transform .35s ease,
    border-color .35s ease;
}

.review-card:hover {

  transform: translateY(-8px);

  border-color:
    rgba(212,175,55,.3);
}

.review-card__header {

  display: flex;

  align-items: center;

  gap: 16px;

  margin-bottom: 20px;
}

.review-avatar {

  width: 70px;
  height: 70px;

  border-radius: 50%;

  display: flex;
  align-items: center;
  justify-content: center;

  font-weight: 800;

  background:
    linear-gradient(
      135deg,
      var(--gold),
      #f7d774
    );

  color: #111;
}

.review-period {

  display: block;

  margin-top: 4px;

  color: var(--muted);

  font-size: .9rem;
}

.review-stars {

  color: var(--gold);

  margin-bottom: 16px;

  letter-spacing: 3px;
}

.review-result {

  display: inline-block;

  margin-bottom: 18px;

  padding: 8px 14px;

  border-radius: 999px;

  background:
    rgba(212,175,55,.12);

  color: var(--gold);

  font-weight: 700;
}

.review-text {

  color: var(--muted);

  line-height: 1.8;
}

@media (max-width: 1100px) {

  .reviews-grid {
    grid-template-columns:
      repeat(2,1fr);
  }
}

@media (max-width: 768px) {

  .testimonials {
    padding: 90px 0;
  }

  .reviews-grid {
    grid-template-columns: 1fr;
  }

  .review-card {
    padding: 24px;
  }

  .review-avatar {
    width: 60px;
    height: 60px;
  }
}
</style>