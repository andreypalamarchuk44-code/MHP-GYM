<template>
  <footer class="footer">

    <div class="footer__glow"></div>

    <div class="container">

      <!-- TOP -->

      <div class="footer__top">

        <h2 class="footer__title">
          Готові змінити своє тіло?
        </h2>

        <p class="footer__subtitle">
          Приєднуйтесь до MHP GYM вже сьогодні та почніть
          шлях до кращої версії себе.
        </p>

        <a
          href="#contact"
          class="footer__cta"
        >
          Записатися на тренування
        </a>

      </div>

      <!-- STATS -->

      <div class="footer__stats">

        <div class="footer-stat">
          <strong>500+</strong>
          <span>Клієнтів</span>
        </div>

        <div class="footer-stat">
          <strong>10+</strong>
          <span>Тренерів</span>
        </div>

        <div class="footer-stat">
          <strong>7</strong>
          <span>Днів на тиждень</span>
        </div>

        <div class="footer-stat">
          <strong>2026</strong>
          <span>Новий рівень фітнесу</span>
        </div>

      </div>

      <!-- MAIN GRID -->

      <div class="footer__grid">

        <!-- BRAND -->

        <div>

          <h3 class="footer__logo">
            MHP <span>GYM</span>
          </h3>

          <p class="footer__description">
            Сучасний фітнес-клуб у Ладижині.
            Сила, дисципліна та результат —
            основа нашої філософії.
          </p>

        </div>

        <!-- MENU -->

        <div>

          <h4 class="footer__heading">
            Навігація
          </h4>

          <nav class="footer__links">

            <a href="#hero">
              Головна
            </a>

            <a href="#programs">
              Напрямки
            </a>

            <a href="#trainers">
              Тренери
            </a>

            <a href="#gallery">
              Галерея
            </a>

            <a href="#membership">
              Абонементи
            </a>

            <a href="#faq">
              FAQ
            </a>

          </nav>

        </div>

        <!-- CONTACTS -->

        <div>

          <h4 class="footer__heading">
            Контакти
          </h4>

          <div class="footer__contacts">

            <p>
              Ладижин, Вінницька область
            </p>

            <a href="tel:+380000000000">
              +380 XX XXX XX XX
            </a>

            <a href="mailto:info@mhpgym.ua">
              info@mhpgym.ua
            </a>

            <p>
              Щодня 07:00 — 22:00
            </p>

          </div>

        </div>

        <!-- SOCIALS -->

        <div>

          <h4 class="footer__heading">
            Соцмережі
          </h4>

          <div class="footer__links">

            <a href="https://instagram.com/mhpgym" target="_blank" rel="noopener" aria-label="Instagram MHP GYM">
              Instagram
            </a>

            <a href="https://facebook.com/mhpgym" target="_blank" rel="noopener" aria-label="Facebook MHP GYM">
              Facebook
            </a>

            <a href="https://t.me/mhpgym" target="_blank" rel="noopener" aria-label="Telegram MHP GYM">
              Telegram
            </a>

            <a href="https://tiktok.com/@mhpgym" target="_blank" rel="noopener" aria-label="TikTok MHP GYM">
              TikTok
            </a>

          </div>

        </div>

      </div>

      <!-- BOTTOM -->

      <div class="footer__bottom">

        <span>
          © 2026 MHP GYM. Всі права захищені.
        </span>

        <span>
          Made with ❤️ in Ukraine
        </span>

      </div>

    </div>

  </footer>
</template>

<style scoped>

.footer {

  position: relative;

  padding:
    120px 0 40px;

  overflow: hidden;

  background:
    linear-gradient(
      180deg,
      #0b0b0b,
      #050505
    );

  border-top:
    1px solid rgba(255,255,255,.06);
}

.footer__glow {

  position: absolute;

  inset: auto;

  top: -250px;
  left: 50%;

  transform:
    translateX(-50%);

  width: 700px;
  height: 700px;

  border-radius: 50%;

  background:
    rgba(212,175,55,.08);

  filter: blur(140px);
}

.footer__top {

  position: relative;
  z-index: 2;

  text-align: center;

  max-width: 800px;

  margin: 0 auto 80px;
}

.footer__title {

  font-size:
    clamp(2rem,5vw,3.5rem);

  margin-bottom: 20px;
}

.footer__subtitle {

  color: var(--muted);

  line-height: 1.8;

  margin-bottom: 30px;
}

.footer__cta {

  display: inline-flex;

  align-items: center;
  justify-content: center;

  padding:
    16px 30px;

  border-radius: 16px;

  background: var(--gold);

  color: #111;

  font-weight: 800;

  text-decoration: none;

  transition: .3s ease;
}

.footer__cta:hover {

  transform:
    translateY(-3px);

  box-shadow:
    0 15px 35px rgba(212,175,55,.25);
}

.footer__stats {

  display: grid;

  grid-template-columns:
    repeat(4,1fr);

  gap: 20px;

  margin-bottom: 80px;
}

.footer-stat {

  padding: 24px;

  text-align: center;

  border-radius: 24px;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);
}

.footer-stat strong {

  display: block;

  font-size: 2rem;

  color: var(--gold);

  margin-bottom: 8px;
}

.footer-stat span {

  color: var(--muted);
}

.footer__grid {

  display: grid;

  grid-template-columns:
    2fr 1fr 1fr 1fr;

  gap: 50px;

  position: relative;
  z-index: 2;
}

.footer__logo {

  font-size: 2rem;

  margin-bottom: 18px;
}

.footer__logo span {

  color: var(--gold);
}

.footer__description {

  max-width: 350px;

  color: var(--muted);

  line-height: 1.8;
}

.footer__heading {

  margin-bottom: 20px;

  font-size: 1rem;
}

.footer__links {

  display: flex;

  flex-direction: column;

  gap: 12px;
}

.footer__links a,
.footer__contacts a {

  color: var(--muted);

  text-decoration: none;

  transition: .3s ease;
}

.footer__links a:hover,
.footer__contacts a:hover {

  color: var(--gold);

  transform:
    translateX(4px);
}

.footer__contacts {

  display: flex;

  flex-direction: column;

  gap: 12px;

  color: var(--muted);
}

.footer__bottom {

  margin-top: 70px;

  padding-top: 25px;

  border-top:
    1px solid rgba(255,255,255,.06);

  display: flex;

  justify-content: space-between;

  gap: 20px;

  color:
    rgba(255,255,255,.45);

  font-size: .9rem;
}

/* Tablet */

@media (max-width: 1100px) {

  .footer__grid {

    grid-template-columns:
      repeat(2,1fr);
  }

  .footer__stats {

    grid-template-columns:
      repeat(2,1fr);
  }
}

/* Mobile */

@media (max-width: 768px) {

  .footer {

    padding:
      90px 0 30px;
  }

  .footer__grid {

    grid-template-columns: 1fr;

    gap: 40px;
  }

  .footer__stats {

    grid-template-columns: 1fr;
  }

  .footer__bottom {

    flex-direction: column;

    text-align: center;
  }

  .footer__top {

    margin-bottom: 60px;
  }
}

</style>