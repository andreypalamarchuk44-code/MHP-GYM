<template>
  <section id="hero" class="hero">

    <!-- VIDEO BACKGROUND -->
    <video
      class="hero__video"
      autoplay
      muted
      loop
      playsinline
      preload="auto"
      poster="@/assets/images/gym-poster.jpg"
    >
      <source src="/videos/gym.mp4" type="video/mp4" />
    </video>

    <!-- OVERLAY -->
    <div class="hero__overlay"></div>

    <!-- GLOW -->
    <div class="hero__glow"></div>

    <div class="container hero__inner">

      <!-- LEFT -->
      <div class="hero__content">

        <span class="hero__eyebrow">
          ФІТНЕС-КЛУБ №1 У МІСТІ
        </span>

        <h1 class="hero__title">
          BUILD YOUR
          <span>STRONGER</span>
          SELF
        </h1>

        <p class="hero__desc">
          Сучасний простір для тих,
          хто прагне сили, енергії та результату.
          Найкраще обладнання,
          професійні тренери та атмосфера перемоги.
        </p>

        <div class="hero__actions">

          <a
            href="#membership"
            class="btn btn-primary"
          >
            Почати сьогодні
          </a>

          <a
            href="#programs"
            class="btn btn-secondary"
          >
            Напрямки
          </a>

        </div>

      </div>

      <!-- RIGHT -->
      <div class="hero__cards">

        <div class="glass-card">

          <strong>07:00 – 22:00</strong>

          <span>
            Щодня, без вихідних
          </span>

        </div>

        <div class="glass-card">

          <strong>Ладижин</strong>

          <span>
            Вінницька область
          </span>

        </div>

        <div class="glass-card glass-card--cta">

          <strong>Перше тренування</strong>

          <span>
            безкоштовно для нових клієнтів
          </span>

        </div>

      </div>

    </div>

    <!-- SCROLL -->
    <div class="hero__scroll">

      <span></span>

    </div>

  </section>
</template>

<style scoped>
.hero {
  position: relative;

  min-height: 100vh;

  display: flex;

  align-items: center;

  overflow: hidden;
}

/* VIDEO */

.hero__video {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  object-fit: cover;
    z-index: 0;

}

/* DARK OVERLAY */

.hero__overlay {
  position: absolute;
  z-index: 1;
  inset: 0;

  background:
    linear-gradient(
      90deg,
      rgba(0,0,0,.88),
      rgba(0,0,0,.55)
    );
}

/* GOLD GLOW */

.hero__glow {
  position: absolute;

  top: 50%;
  right: -200px;

  width: 600px;
  height: 600px;
  z-index: 1;
  border-radius: 50%;

  background:
    radial-gradient(
      circle,
      rgba(212,175,55,.18),
      transparent 70%
    );
}

.hero__inner {
  position: relative;

  z-index: 2;

  width: 100%;

  display: grid;

  grid-template-columns:
    1.2fr
    .8fr;

  gap: 80px;

  align-items: center;
}

.hero__eyebrow {
  color: var(--gold);

  font-size: 13px;

  font-weight: 700;

  letter-spacing: .25em;

  text-transform: uppercase;
}

.hero__title {
  margin: 20px 0;

  font-size:
    clamp(
      3rem,
      8vw,
      7rem
    );

  line-height: .9;

  font-weight: 900;
}

.hero__title span {
  color: var(--gold);
}

.hero__desc {
  max-width: 650px;

  color: rgba(255,255,255,.8);

  line-height: 1.9;

  margin-bottom: 40px;

  font-size: 1.05rem;
}

.hero__actions {
  display: flex;

  gap: 16px;
}

/* FLOATING CARDS */

.hero__cards {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.glass-card {
  padding: 18px 20px;
  border-radius: 18px;

  background: rgba(255,255,255,0.06);
  backdrop-filter: blur(14px);

  border: 1px solid rgba(255,255,255,0.08);

  color: #fff;

  transition: transform .35s ease, border-color .35s ease;

  position: relative;
  overflow: hidden;
}

.glass-card--cta {
  border-color: rgba(212,175,55,0.4);
  background: rgba(212,175,55,0.08);
}
/* glow hover layer */
.glass-card::before {
  content: "";
  position: absolute;
  inset: 0;

  background: linear-gradient(
    135deg,
    rgba(212,175,55,0.0),
    rgba(212,175,55,0.15)
  );

  opacity: 0;
  transition: .35s ease;
}

/* HOVER EFFECT */
.glass-card:hover {
  transform: translateY(-4px);
  border-color: rgba(212,175,55,0.5);
}

.glass-card:hover::before {
  opacity: 1;
}

.glass-card strong {
  display: block;
  font-size: 22px;
  color: var(--gold, #d4af37);
}

.glass-card span {
  font-size: 14px;
  opacity: .75;
}


/* SCROLL */

.hero__scroll {
  position: absolute;

  left: 50%;
  bottom: 30px;

  transform: translateX(-50%);
}

.hero__scroll span {
  display: block;

  width: 2px;
  height: 50px;

  background: var(--gold);

  animation:
    scrollLine
    1.5s
    infinite;
}

@keyframes scrollLine {

  0% {
    opacity: .2;
    transform: scaleY(.4);
  }

  50% {
    opacity: 1;
    transform: scaleY(1);
  }

  100% {
    opacity: .2;
    transform: scaleY(.4);
  }
}

/* TABLET */

@media(max-width:992px){

  .hero__inner{
    grid-template-columns:1fr;
  }

  .hero__cards{
    flex-direction:row;
  }
}

/* MOBILE */

@media(max-width:768px){

  .hero{
    padding-top:120px;
  }

  .hero__actions{
    flex-direction:column;
  }

  .hero__cards{
    flex-direction:column;
  }

  .glass-card{
    padding:22px;
  }

  .hero__title{
    font-size:3.5rem;
  }
}
</style>