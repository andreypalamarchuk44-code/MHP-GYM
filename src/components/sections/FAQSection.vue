<template>
  <section
    id="faq"
    class="faq"
  >
    <div class="container">

      <span class="section-eyebrow">
        FAQ
      </span>

      <h2 class="section-title">
        Часті запитання
      </h2>

      <p class="faq__subtitle">
        Відповіді на найпоширеніші питання
        про тренування та абонементи.
      </p>

      <div class="faq__list">

        <article
          v-for="(item, index) in faqItems"
          :key="index"
          class="faq-item"
          :class="{ active: activeIndex === index }"
        >

          <button
            class="faq-item__header"
            @click="toggle(index)"
          >

            <span>
              {{ item.question }}
            </span>

            <span class="faq-item__icon">
              {{ activeIndex === index ? '−' : '+' }}
            </span>

          </button>

          <Transition name="faq">

            <div
              v-if="activeIndex === index"
              class="faq-item__content"
            >

              <p>
                {{ item.answer }}
              </p>

            </div>

          </Transition>

        </article>

      </div>

    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeIndex = ref(0)

const faqItems = [
  {
    question: 'Чи є пробне тренування?',
    answer:
      'Так, кожен новий клієнт може відвідати пробне тренування та познайомитися із залом.'
  },
  {
    question: 'Чи допомагаєте зі складанням програми?',
    answer:
      'Наші тренери складають індивідуальні програми залежно від ваших цілей.'
  },
  {
    question: 'Чи є персональні тренування?',
    answer:
      'Так, доступні персональні тренування з досвідченими тренерами.'
  },
  {
    question: 'Який графік роботи залу?',
    answer:
      'Щодня з 07:00 до 22:00 без вихідних.'
  },
  {
    question: 'Чи є душові та роздягальні?',
    answer:
      'Так, у клубі обладнані сучасні роздягальні та душові кімнати.'
  }
]

function toggle(index) {
  activeIndex.value =
    activeIndex.value === index
      ? null
      : index
}
</script>

<style scoped>

.faq {
  padding: 120px 0;
}

.faq__subtitle {
  margin-top: 16px;
  max-width: 700px;
  color: var(--muted);
}

.faq__list {
  margin-top: 60px;

  display: flex;
  flex-direction: column;
  gap: 18px;
}

.faq-item {

  border-radius: 24px;

  overflow: hidden;

  background:
    rgba(255,255,255,.03);

  border:
    1px solid rgba(255,255,255,.06);

  transition:
    border-color .3s ease,
    transform .3s ease;
}

.faq-item.active {

  border-color:
    rgba(212,175,55,.3);
}

.faq-item:hover {

  transform: translateY(-2px);
}

.faq-item__header {

  width: 100%;

  border: none;

  background: transparent;

  color: inherit;

  cursor: pointer;

  padding: 24px 30px;

  display: flex;

  align-items: center;
  justify-content: space-between;

  text-align: left;

  font-size: 1.05rem;

  font-weight: 700;
}

.faq-item__icon {

  font-size: 1.5rem;

  color: var(--gold);

  flex-shrink: 0;

  margin-left: 20px;
}

.faq-item__content {

  padding:
    0 30px 28px;

  color: var(--muted);

  line-height: 1.8;
}

.faq-enter-active,
.faq-leave-active {

  transition:
    opacity .25s ease,
    transform .25s ease;
}

.faq-enter-from,
.faq-leave-to {

  opacity: 0;

  transform:
    translateY(-10px);
}

@media(max-width:768px){

  .faq {
    padding: 90px 0;
  }

  .faq-item__header {

    padding:
      20px 22px;

    font-size: 1rem;
  }

  .faq-item__content {

    padding:
      0 22px 22px;
  }
}
</style>