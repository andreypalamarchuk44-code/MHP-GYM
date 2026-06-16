<template>
  <section
    id="contact"
    class="contact"
  >
    <div class="container">

      <div class="contact__grid">

        <!-- LEFT -->

        <div class="contact__content">

          <span class="section-eyebrow">
            Контакти
          </span>

          <h2 class="section-title">
            Почніть тренуватись вже сьогодні
          </h2>

          <p class="contact__subtitle">
            Запишіться на пробне тренування або
            зв'яжіться з нами будь-яким зручним способом.
          </p>

          <div class="contact__cards">

            <div class="contact-card">

              <div class="contact-card__icon">
                <i class="fa-solid fa-location-dot"></i>
              </div>

              <div>
                <h3>Адреса</h3>

                <p>
                  Ладижин, Вінницька область
                </p>
              </div>

            </div>

            <div class="contact-card">

              <div class="contact-card__icon">
                <i class="fa-solid fa-phone"></i>
              </div>

              <div>
                <h3>Телефон</h3>

                <a href="tel:+380000000000">
                  +380 XX XXX XX XX
                </a>
              </div>

            </div>

            <div class="contact-card">

              <div class="contact-card__icon">
                <i class="fa-solid fa-envelope"></i>
              </div>

              <div>
                <h3>Email</h3>

                <a href="mailto:info@mhpgym.ua">
                  info@mhpgym.ua
                </a>
              </div>

            </div>

            <div class="contact-card">

              <div class="contact-card__icon">
                <i class="fa-solid fa-clock"></i>
              </div>

              <div>
                <h3>Графік роботи</h3>

                <p>
                  Щодня 07:00 — 22:00
                </p>
              </div>

            </div>

          </div>

        </div>

        <!-- RIGHT -->

        <div class="contact__form-wrap">

          <h3 class="contact__form-title">
            Запис на пробне тренування
          </h3>

          <p class="contact__form-text">
            Залиште заявку і ми зв'яжемося з вами.
          </p>

          <form
            class="contact__form"
            @submit.prevent="submitForm"
          >

            <input
              v-model="form.name"
              type="text"
              placeholder="Ваше ім'я"
              required
            >

            <input
              v-model="form.phone"
              type="tel"
              placeholder="Телефон"
              required
            >

            <input
              v-model="form.email"
              type="email"
              placeholder="Email (необов'язково)"
            >

            <textarea
              v-model="form.message"
              rows="5"
              placeholder="Ваше повідомлення"
            ></textarea>

            <button
              type="submit"
              class="contact__btn"
              :disabled="sending"
            >
              {{ sending ? 'Надсилаємо…' : 'Надіслати заявку' }}
            </button>

            <p v-if="sent" class="contact__form-success">
              Дякуємо! Заявку відкрито у вашому email-клієнті — підтвердіть відправку.
            </p>

          </form>

        </div>

      </div>

      <!-- MAP -->

      <div class="contact__map">

        <iframe
          src="https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d202.57760191846992!2d29.235093024436868!3d48.68345984829952!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x40cd705e13c13db3%3A0xf374e367a967e2a4!2z0KDRj9Cx0LAgR3lt!5e1!3m2!1sru!2sua!4v1781610141133!5m2!1sru!2sua"
          loading="lazy"
          allowfullscreen
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>

      </div>

    </div>
  </section>
</template>

<script setup>
import { reactive, ref, onMounted, onUnmounted } from 'vue'

const form = reactive({
  name: '',
  phone: '',
  email: '',
  message: '',
  plan: ''
})

const sending = ref(false)
const sent = ref(false)

function handlePlanSelected(e) {
  form.plan = e.detail
  form.message = `Цікавить тариф "${e.detail}". ${form.message}`.trim()
}

onMounted(() => {
  window.addEventListener('plan-selected', handlePlanSelected)
})

onUnmounted(() => {
  window.removeEventListener('plan-selected', handlePlanSelected)
})

function submitForm() {
  sending.value = true

  const subject = encodeURIComponent('Заявка на пробне тренування — MHP GYM')
  const bodyLines = [
    `Ім'я: ${form.name}`,
    `Телефон: ${form.phone}`,
    form.email ? `Email: ${form.email}` : null,
    form.plan ? `Обраний тариф: ${form.plan}` : null,
    form.message ? `Повідомлення: ${form.message}` : null
  ].filter(Boolean)
  const body = encodeURIComponent(bodyLines.join('\n'))

  window.location.href = `mailto:info@mhpgym.ua?subject=${subject}&body=${body}`

  sending.value = false
  sent.value = true

  setTimeout(() => {
    sent.value = false
  }, 6000)
}
</script>

<style scoped>

.contact {
  padding: 120px 0;
}

.contact__grid {

  display: grid;

  grid-template-columns:
    1.1fr .9fr;

  gap: 60px;

  align-items: start;
}

.contact__subtitle {

  margin-top: 18px;

  max-width: 600px;

  color: var(--muted);

  line-height: 1.8;
}

.contact__cards {

  margin-top: 40px;

  display: grid;

  grid-template-columns:
    repeat(2,1fr);

  gap: 20px;
}

.contact-card {

  display: flex;

  gap: 16px;

  padding: 22px;

  border-radius: 24px;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);

  transition: .3s ease;
}

.contact-card:hover {

  transform: translateY(-4px);

  border-color:
    rgba(212,175,55,.3);
}

.contact-card__icon {

  width: 46px;
  height: 46px;

  flex-shrink: 0;

  display: flex;
  align-items: center;
  justify-content: center;

  border-radius: 14px;

  background:
    rgba(212,175,55,.12);

  color: var(--gold);

  font-size: 1.1rem;
}

.contact-card h3 {

  margin-bottom: 8px;

  font-size: 1rem;
}

.contact-card p,
.contact-card a {

  color: var(--muted);

  text-decoration: none;
}

.contact__form-wrap {

  padding: 34px;

  border-radius: 30px;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);
}

.contact__form-title {

  margin-bottom: 10px;

  font-size: 1.6rem;
}

.contact__form-text {

  color: var(--muted);

  margin-bottom: 28px;
}

.contact__form {

  display: flex;

  flex-direction: column;

  gap: 16px;
}

.contact__form input,
.contact__form textarea {

  width: 100%;

  border: none;

  outline: none;

  border-radius: 16px;

  padding: 16px 20px;

  color: white;

  background:
    rgba(255,255,255,.05);

  border:
    1px solid rgba(255,255,255,.08);

  transition: .3s ease;
}

.contact__form input:focus,
.contact__form textarea:focus {

  border-color: var(--gold);
}

.contact__form textarea {

  resize: vertical;

  min-height: 140px;
}

.contact__btn {

  border: none;

  cursor: pointer;

  padding: 18px;

  border-radius: 16px;

  font-weight: 800;

  background: var(--gold);

  color: black;

  transition: .3s ease;
}

.contact__btn:hover {

  transform: translateY(-2px);
}

.contact__btn:disabled {

  opacity: .6;

  cursor: not-allowed;

  transform: none;
}

.contact__form-success {

  margin-top: 4px;

  padding: 14px 16px;

  border-radius: 14px;

  background:
    rgba(212,175,55,.12);

  border:
    1px solid rgba(212,175,55,.3);

  color: var(--gold);

  font-size: .92rem;

  line-height: 1.5;
}

.contact__map {

  margin-top: 80px;

  overflow: hidden;

  border-radius: 30px;

  border:
    1px solid rgba(255,255,255,.08);

  box-shadow:
    0 25px 50px rgba(0,0,0,.25);
}

.contact__map iframe {

  width: 100%;

  height: 550px;

  border: none;

  display: block;
}

/* Tablet */

@media (max-width: 1100px) {

  .contact__grid {

    grid-template-columns: 1fr;
  }
}

/* Mobile */

@media (max-width: 768px) {

  .contact {
    padding: 90px 0;
  }

  .contact__cards {

    grid-template-columns: 1fr;
  }

  .contact__form-wrap {

    padding: 24px;
  }

  .contact__map {

    margin-top: 50px;
  }

  .contact__map iframe {

    height: 350px;
  }
}
</style>