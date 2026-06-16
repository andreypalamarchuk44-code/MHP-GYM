<template>
  <section
    id="programs"
    class="programs"
  >

    <div class="container">

      <span class="section-eyebrow">
        Напрямки
      </span>

      <h2 class="section-title">
        Обери свій шлях до результату
      </h2>

      <div class="programs__grid">

        <article
          v-for="program in programs"
          :key="program.id"
          class="program"
        >

          <h3>{{ program.title }}</h3>

          <p>{{ program.description }}</p>

        </article>

      </div>

    </div>

  </section>
</template>

<script setup>
import programs from '@/data/programs'
</script>

<style scoped>
.programs {
  background: var(--surface);
}

.programs__grid {
  margin-top: 60px;

  display: grid;

  grid-template-columns: repeat(4,1fr);

  gap: 24px;
}

.program {
  background: var(--card);

  padding: 35px;

  border-radius: 24px;

  transition: .3s;

  border: 1px solid transparent;
}

.program:hover {
  transform: translateY(-8px);

  border-color: rgba(212,175,55,.3);
}

.program h3 {
  font-size: 1.3rem;

  margin-bottom: 16px;
}

.program p {
  color: var(--muted);

  line-height: 1.8;
}

@media(max-width:992px){
  .programs__grid{
    grid-template-columns:repeat(2,1fr);
  }
}

@media(max-width:576px){
  .programs__grid{
    grid-template-columns:1fr;
  }
}
</style>