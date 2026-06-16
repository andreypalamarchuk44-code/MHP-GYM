<template>
  <section
    id="trainers"
    class="trainers"
  >
    <div class="container">

      <span class="section-eyebrow">
        Команда
      </span>

      <h2 class="section-title">
        Тренери MHP GYM
      </h2>

      <p class="trainers__subtitle">
        Професіонали, які допоможуть
        досягти ваших цілей швидше.
      </p>

      <div class="trainers__grid">

        <article
          v-for="trainer in trainers"
          :key="trainer.id"
          class="trainer-card"
        >

          <div class="trainer-card__image">

            <img
              :src="trainer.image"
              :alt="trainer.name"
            >

            <div class="trainer-card__overlay">

              <a
                :href="trainer.instagram"
                target="_blank"
                rel="noopener"
                class="trainer-card__social"
              >
                Instagram
              </a>

            </div>

          </div>

          <div class="trainer-card__content">

            <h3>
              {{ trainer.name }}
            </h3>

            <span class="trainer-role">
              {{ trainer.role }}
            </span>

            <div class="trainer-meta">

              <div>
                <strong>
                  Досвід
                </strong>

                <span>
                  {{ trainer.experience }}
                </span>
              </div>

              <div>
                <strong>
                  Напрямок
                </strong>

                <span>
                  {{ trainer.specialty }}
                </span>
              </div>

            </div>

          </div>

        </article>

      </div>

    </div>
  </section>
</template>

<script setup>
import trainers from '@/data/trainers'
</script>

<style scoped>

.trainers {
  padding: 120px 0;
}

.trainers__subtitle {
  max-width: 700px;
  margin-top: 16px;
  color: var(--muted);
}

.trainers__grid {
  margin-top: 60px;

  display: grid;

  grid-template-columns:
    repeat(4,1fr);

  gap: 24px;
}

.trainer-card {

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);

  border-radius: 28px;

  overflow: hidden;

  transition:
    transform .35s ease,
    border-color .35s ease;
}

.trainer-card:hover {
  transform: translateY(-8px);

  border-color:
    rgba(212,175,55,.35);
}

.trainer-card__image {
  position: relative;

  height: 380px;

  overflow: hidden;
}

.trainer-card__image img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  transition: .6s ease;
}

.trainer-card:hover
.trainer-card__image img {
  transform: scale(1.08);
}

.trainer-card__overlay {

  position: absolute;
  inset: 0;

  display: flex;

  align-items: center;
  justify-content: center;

  background:
    rgba(0,0,0,.55);

  opacity: 0;

  transition: .35s ease;
}

.trainer-card:hover
.trainer-card__overlay {
  opacity: 1;
}

.trainer-card__social {

  background: var(--gold);

  color: black;

  text-decoration: none;

  padding: 12px 20px;

  border-radius: 999px;

  font-weight: 700;
}

.trainer-card__content {
  padding: 24px;
}

.trainer-card h3 {
  margin-bottom: 8px;
}

.trainer-role {
  color: var(--gold);

  font-size: .95rem;
}

.trainer-meta {
  margin-top: 20px;

  display: flex;

  flex-direction: column;

  gap: 16px;
}

.trainer-meta strong {
  display: block;

  margin-bottom: 4px;
}

.trainer-meta span {
  color: var(--muted);
}

@media(max-width:1200px){

  .trainers__grid{
    grid-template-columns:
      repeat(2,1fr);
  }
}

@media(max-width:768px){

  .trainers {
    padding: 90px 0;
  }

  .trainers__grid{
    grid-template-columns:1fr;
  }

  .trainer-card__image{
    height:320px;
  }
}
</style>