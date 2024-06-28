<template>
  <main class="main">
    <div class="main-container">
      <section class="traffic-masters">
        <div class="title-wrap">
          <img class="title-hand" src="~assets/icons/hand.svg" alt="left hand" />
          <h1 class="traffic-masters-title">Володарі Трафіку</h1>
          <img class="title-hand right-hand" src="~assets/icons/hand.svg" alt="right hand" />
        </div>
        <p class="traffic-masters-disc">
          SC Partners – нова партнерська мережа з величезним досвідом та
          експертизою. Кожен наш партнер отримує очікувану вигоду на абсолютно
          прозорих умовах та бездоганний супровід. Ми будемо поряд з вами: на
          відстані одного повідомлення в месенджері або дзвінка, адже ми
          працюємо поряд з вами.
        </p>
        <div class="stars">
          <span v-for="star in 5" :key="star"></span>
        </div>
      </section>
      <section class="information">
        <h2 class="information-title">Тим, хто нагоняє Траф</h2>
        <ul class="information-list">
          <li class="information-item">
            <div class="information-item-icon megaphone"></div>
            <div class="information-item-text-block">
              <h3 class="information-item-title">
                Круті акції, призи та прибуткова бонусна програма
              </h3>
              <p class="information-item-disc">
                Ми постійно працюємо над тим, щоб вам було цікаво та вигідно!
              </p>
            </div>
          </li>
          <li class="information-item">
            <div class="information-item-icon smile"></div>
            <div class="information-item-text-block">
              <h3 class="information-item-title">
                Особлива підтримка<br />
                для кожного 24/7
              </h3>
              <p class="information-item-disc">
                У вас буде свій персональний менеджер
              </p>
            </div>
          </li>
          <li class="information-item">
            <div class="information-item-icon graph"></div>
            <div class="information-item-text-block">
              <h3 class="information-item-title br">Детальна статистика</h3>
              <p class="information-item-disc">
                Миттєве оновлення, зрозуміла система відображення статистики
              </p>
            </div>
          </li>
        </ul>
      </section>
    </div>
  </main>
</template>

<style>
.main-container {
  display: flex;
  flex-direction: column;
  max-width: 1200px;
  margin: 100px auto 0;
}

.traffic-masters {
  position: relative;
  display: flex;
  flex-direction: column;
  row-gap: 25px;
  align-items: center;
  max-width: 900px;
  padding: 39px 44px;
  margin: 0 auto 125px;
  background-color: #23262f80;
  border-radius: 24px;
}

.traffic-masters::before {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  content: '';
  background-image: url('~assets/img/graph.webp');
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}

.title-wrap {
  display: flex;
  gap: 25px;
}

.title-hand {
  object-fit: contain;
}

.right-hand {
  transform: rotateY(180deg);
}

.traffic-masters-title {
  font-family: var(--gilroy);
  font-size: 40px;
  font-weight: 700;
  line-height: 48px;
  color: var(--gray-200);
}

.traffic-masters-disc {
  max-width: 812px;
  font-family: var(--roboto);
  line-height: 24px;
  text-align: center;
  word-wrap: break-word;
}

.stars {
  display: flex;
  gap: 25px;
}

.stars span {
  display: block;
  width: 15px;
  height: 15px;
  background-image: url('~assets/icons/icon_star.svg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}

.information {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 100px;
}

.information-title {
  margin-bottom: 75px;
  font-family: var(--gilroy);
  font-size: 32px;
  font-weight: 700;
  line-height: 40px;
  color: var(--gray-200);
}

.information-list {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.information-item {
  display: flex;
  flex-direction: column;
  row-gap: 25px;
  align-items: center;
  width: 345px;
}

.information-item-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 65px;
  height: 65px;
  background-color: var(--yellow);
  border-radius: 15px;
}

.megaphone,
.smile,
.graph {
  background-image: url('~assets/icons/icon_megaphone.svg');
  background-repeat: no-repeat;
  background-position: center;
}

.smile {
  background-image: url('~assets/icons/icon_smile.svg');
}

.graph {
  background-image: url('~assets/icons/icon_graph.svg');
}

.information-item-text-block {
  display: flex;
  flex-direction: column;
  gap: 25px;
  align-items: center;
  justify-content: center;
}

.information-item-title {
  width: 250px;
  font-family: var(--roboto);
  font-size: 16px;
  font-weight: 500;
  line-height: 24px;
  color: var(--gray-400);
  text-align: center;
  word-wrap: break-word;
}

.br {
  width: 140px;
}

.information-item-disc {
  font-family: var(--gray-500);
  text-align: center;
  word-wrap: break-word;
}

@media (width <=1023px) {
  .main-container {
    padding: 0 15px 50px;
  }
}

@media (width >=375px) and (width <=767px) {
  .main-container {
    flex-direction: column-reverse;
    margin-top: 50px;
  }

  .information {
    padding-bottom: 50px;
  }

  .information-title {
    margin-bottom: 35px;
    font-size: 25px;
    line-height: 25px;
  }

  .information-list {
    flex-flow: column wrap;
    gap: 25px;
    align-items: center;
  }

  .information-item {
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
  }

  .information-item-icon {
    width: 45px;
    height: 45px;
    background-size: 25px;
  }

  .information-item-text-block {
    gap: 5px;
    width: 245px;
  }

  .information-item-title,
  .information-item-disc {
    width: 100%;
    text-align: left;
  }

  .br {
    width: 100%;
  }

  .traffic-masters {
    padding: 24px;
    margin-bottom: 0;
  }

  .title-wrap {
    gap: 10px;
  }

  .traffic-masters-title {
    font-size: 25px;
    line-height: 25px;
  }

  .title-hand {
    width: 20px;
  }
}
</style>
