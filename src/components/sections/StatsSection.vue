<template>
  <section class="stats">

    <div class="container">

      <div class="stats__grid">

        <div class="stat-card">
          <h3>2000+</h3>
          <p>Активних клієнтів</p>
        </div>

        <div class="stat-card">
          <h3>80+</h3>
          <p>Професійних тренажерів</p>
        </div>

        <div class="stat-card">
          <h3>10+</h3>
          <p>Років досвіду</p>
        </div>

        <div class="stat-card">
          <h3>7/7</h3>
          <p>Працюємо щодня</p>
        </div>

      </div>

    </div>

  </section>
</template>

<style scoped>
.stats {
  padding: 0 0 120px;
}

.stats__grid {
  display: grid;
  grid-template-columns: repeat(4,1fr);
  gap: 24px;
}

.stat-card {
  background: var(--card);

  border-radius: 24px;

  padding: 40px;

  text-align: center;

  border: 1px solid rgba(255,255,255,.05);

  transition: .3s;
}

.stat-card:hover {
  transform: translateY(-8px);

  border-color: rgba(212,175,55,.3);
}

.stat-card h3 {
  font-size: 3rem;

  color: var(--gold);

  margin-bottom: 12px;
}

.stat-card p {
  color: var(--muted);
}

@media(max-width:992px){
  .stats__grid{
    grid-template-columns:repeat(2,1fr);
  }
}

@media(max-width:576px){
  .stats__grid{
    grid-template-columns:1fr;
  }
}
</style>