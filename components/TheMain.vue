<template>
  <main class="main">
    <div class="main-container">
      <section class="traffic-masters">
        <div class="title-wrap">
          <img src="~assets/img/hand.svg" class="title-hand" alt="left hand" />
          <h1 class="traffic-masters-title">Володарі Трафіку</h1>
          <img
            src="~assets/img/hand.svg"
            class="title-hand right-hand"
            alt="right hand"
          />
        </div>
        <p class="traffic-masters-disc">
          SC Partners – нова партнерська мережа з величезним досвідом та
          експертизою. Кожен наш партнер отримує очікувану вигоду на абсолютно
          прозорих умовах та бездоганний супровід. Ми будемо поряд з вами: на
          відстані одного повідомлення в месенджері або дзвінка, адже ми
          працюємо поряд з вами.
        </p>
        <div class="stars" filled>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
          <span class="icon-star"></span>
        </div>
      </section>
      <section class="information">
        <h2 class="information-title">Тим, хто нагоняє Траф</h2>
        <ul class="information-list">
          <li class="information-item">
            <div class="information-item-icon megaphone"></div>
            <div class="information-text-block">
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
            <div class="information-text-block">
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
            <div class="information-text-block">
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
  max-width: 1200px;
  display: flex;
  flex-direction: column;
  margin: 100px auto 0;
}

.traffic-masters {
  position: relative;
  max-width: 900px;
  padding: 39px 44px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 auto 125px auto;
  border-radius: 24px;
  row-gap: 25px;
  background-color: #23262f80;
}

.traffic-masters::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url('~assets/img/graph.png');
  background-position: center;
  background-repeat: no-repeat;
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
  font-family: var(--roboto);
  line-height: 24px;
  text-align: center;
}

.stars {
  display: flex;
  gap: 25px;
}

.icon-star {
  position: relative;
  display: block;
  width: 15px;
  height: 15px;
}

.icon-star::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url('~assets/icons/icon_star.svg');
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}

.information {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 100px;
}

.information-title {
  font-family: var(--gilroy);
  color: var(--gray-200);
  font-size: 32px;
  font-weight: 700;
  line-height: 40px;
  margin-bottom: 75px;
}

.information-list {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.information-item {
  width: 345px;
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 25px;
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

.information-text-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 25px;
}

.information-item-title {
  width: 250px;
  font-family: var(--roboto);
  font-size: 16px;
  font-weight: 500;
  line-height: 24px;
  text-align: center;
  color: var(--gray-400);
}

.br {
  width: 140px;
}

.information-item-disc {
  font-family: var(--gray-500);
  text-align: center;
}

@media (max-width: 1023px) {
  .main-container {
    padding: 10px;
  }
}

@media (min-width: 375px) and (max-width: 767px) {
  .main-container {
    margin-top: 50px;
    flex-direction: column-reverse;
  }

  .information {
    padding-bottom: 50px;
  }

  .information-title {
    font-size: 25px;
    line-height: 25px;
    margin-bottom: 35px;
  }

  .information-list {
    flex-wrap: wrap;
    flex-direction: column;
    align-items: center;
    gap: 25px;
  }

  .information-item {
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
  }

  .information-item-icon {
    width: 45px;
    height: 45px;
  }

  .information-text-block {
    width: 245px;
    gap: 5px;
  }

  .information-item-title,
  .information-item-disc {
    text-align: left;
    width: 100%;
  }

  .br {
    width: 100%;
  }

  .traffic-masters {
    padding: 27px;
    margin-bottom: 35px;
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
