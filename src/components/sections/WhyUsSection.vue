<template>
  <section class="why-us">

    <div class="container">

      <span class="section-eyebrow">
        Чому саме ми
      </span>

      <h2 class="section-title">
        MHP GYM — новий стандарт
        фітнесу у місті
      </h2>

      <div class="why-us__grid">

        <div class="why-card">
          <span>01</span>
          <h3>Преміальне обладнання</h3>
        </div>

        <div class="why-card">
          <span>02</span>
          <h3>Сертифіковані тренери</h3>
        </div>

        <div class="why-card">
          <span>03</span>
          <h3>Велика кардіо зона</h3>
        </div>

        <div class="why-card">
          <span>04</span>
          <h3>Комфортні роздягальні</h3>
        </div>

        <div class="why-card">
          <span>05</span>
          <h3>Персональні програми</h3>
        </div>

        <div class="why-card">
          <span>06</span>
          <h3>Доступні абонементи</h3>
        </div>

      </div>

    </div>

  </section>
</template>

<style scoped>
.why-us__grid {
  margin-top: 60px;

  display: grid;

  grid-template-columns: repeat(3,1fr);

  gap: 24px;
}

.why-card {
  background: linear-gradient(
    145deg,
    rgba(255,255,255,.03),
    rgba(255,255,255,.01)
  );

  padding: 36px;

  border-radius: 24px;

  border: 1px solid rgba(255,255,255,.05);

  transition: .3s;
}

.why-card:hover {
  transform: translateY(-8px);
}

.why-card span {
  display: inline-block;

  margin-bottom: 20px;

  font-size: 2rem;

  color: var(--gold);

  font-weight: 800;
}

.why-card h3 {
  font-size: 1.2rem;
}

@media(max-width:992px){
  .why-us__grid{
    grid-template-columns:repeat(2,1fr);
  }
}

@media(max-width:576px){
  .why-us__grid{
    grid-template-columns:1fr;
  }
}
</style>