<template>
  <div class="registration-container">
    <div class="registration-wrapper">
      <div class="close-form close-registration">
        <span class="close-line"></span>
      </div>
      <div class="registration-slider">
        <div class="reg-slider-container">
          <div class="reg-slider-wrap">
            <div class="slider-element">
              <h3 class="slider-element-title">Зможеш обрати свій варіант</h3>
              <ul class="slider-list">
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">CPA</h4>
                    <p class="list-item-disc">$25 і вище</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">REVSHARE</h4>
                    <p class="list-item-disc">Піднімай до 60%</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">Гібрід</h4>
                    <p class="list-item-disc">Зробимо як скажеш</p>
                  </div>
                </li>
              </ul>
            </div>
            <div class="slider-element">
              <h3 class="slider-element-title">Lorem ipsum dolor sit.</h3>
              <ul class="slider-list">
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">Lorem.</h4>
                    <p class="list-item-disc">$25 Lorem, ipsum.</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">REVSHARE</h4>
                    <p class="list-item-disc">Lorem, ipsum. 60%</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">Гібрід</h4>
                    <p class="list-item-disc">Lorem, ipsum dolor.</p>
                  </div>
                </li>
              </ul>
            </div>
            <div class="slider-element">
              <h3 class="slider-element-title">Lorem ipsum dolor sit.</h3>
              <ul class="slider-list">
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">CPA</h4>
                    <p class="list-item-disc">$25 Lorem, ipsum.</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">REVSHARE</h4>
                    <p class="list-item-disc">Lorem, ipsum. 60%</p>
                  </div>
                </li>
                <li class="slider-list-item">
                  <div class="list-item-icon"></div>
                  <div class="list-item-text">
                    <h4 class="list-item-title">Lorem.</h4>
                    <p class="list-item-disc">Lorem, ipsum dolor.</p>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <div class="slider-pagination-wrap">
          <button class="slider-btn-prew slider-btn"></button>
          <div class="pagination-dots">
            <span class="pagination-dot"></span>
            <span class="pagination-dot"></span>
            <span class="pagination-dot"></span>
          </div>
          <button class="slider-btn-next slider-btn"></button>
        </div>
      </div>
      <div class="registration-form">
        <div class="registration-title-wrapper">
          <div class="registration-icon"></div>
          <p class="registration-form-title">Реєстрація</p>
        </div>

        <form action="#" method="post" class="registration-form">
          <fieldset class="fieldset-box">
            <input
                class="input-style"
                type="text"
                name="name"
                id="name"
                placeholder="Ваше імʼя"
              />
            <label for="name"><span class="name-icon"></span></label>
            <input
                class="input-style"
                type="email"
                name="email"
                id="email"
                placeholder="Ваш email"
              />
            <label for="email"><span class="email-icon"></span></label>
            <input
                class="input-style"
                type="password"
                name="password"
                id="password"
                placeholder="Ваш пароль"
              />
            <label for="password">
              <p class="password-error">Пароль має містити літери і символи</p>
              <span class="show-password"></span>
            </label>
            <input
                class="input-style"
                type="password"
                name="check-password"
                id="check-password"
                placeholder="Повторіть пароль"
              />
            <label for="check-password">
              <p class="check-password-error">Паролі не співпадають</p>
              <span class="show-password"></span>
            </label>
            <div class="choose-messenger">
              <p class="messenger-tilte">Оберіть спосіб звязку</p>
              <div class="communication-method">
                  <input type="radio" id="telegram" name="messenger" value="telegram" checked>
                  <label for="telegram" class="telegram"></label>
                  <input type="radio" id="skype" name="messenger" value="skype" >
                  <label for="skype" class="skype"></label>
                  <input
                    type="text"
                    id="messenger-link"
                    name="messenger-link"
                    class="input-style messenger-input"
                    placeholder="@телеграм_адреса"
                  />
                <label for="messenger-link"><span class="messenger-icon"></span></label>
              </div>
            </div>
            <button type="submit" class="btn-submit-reg-form">
              Реєстрація
            </button>
          </fieldset>
        </form>
      </div>
    </div>
  </div>
</template>

<style>
.registration-container {
  position: absolute;
  z-index: 5;
  width: 100%;
  height: 100%;
  background-color: rgba(53, 57, 69, 0.9);
  display: none;
  align-items: center;
  justify-content: center;
}
.registration-wrapper {
  position: relative;
  max-width: 770px;
  display: flex;
  border-radius: 25px;
}
.registration-slider {
  width: 385px;
  background-color: var(--green);
  background-image: url('~assets/img/slider_bg.png');
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  border-bottom-left-radius: 25px;
  border-top-left-radius: 25px;
}
.reg-slider-container {
  width: 220px;
  height: 330px;
  margin: 65px 0 82px 53px;
  position: relative;
  overflow: hidden;
}
.reg-slider-wrap {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  transition: 500ms ease;
}
.slider-element {
  width: 220px;
}
.slider-element-title {
  font-family: var(--gilroy);
  font-size: 25px;
  font-weight: 400;
  line-height: 40px;
  color: var(--gray-100);
  margin-bottom: 65px;
}
.slider-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.slider-list-item {
  display: flex;
}
.list-item-icon {
  width: 45px;
  height: 45px;
  background-color: #ffffff33;
  border-radius: 50%;
  position: relative;
  margin-right: 25px;
}
.list-item-icon::after {
  content: '';
  width: 24px;
  height: 24px;
  position: absolute;
  top: 10px;
  left: 10px;
  background-image: url('~assets/icons/line.svg');
}
.list-item-title {
  font-family: var(--gilroy);
  font-size: 14px;
  font-weight: 700;
  line-height: 16px;
  color: var(--gray-100);
}
.list-item-disc {
  font-family: var(--roboto);
  font-size: 14px;
  font-weight: 400;
  line-height: 24px;
  color: var(--gray-100);
}

.slider-pagination-wrap {
  margin: 0 auto;
  width: 96px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 107px;
}
.pagination-wrap {
  display: flex;
}
.pagination-dots {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}
.pagination-dot {
  display: block;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #fff;
  cursor: pointer;
}
.dot-active {
  background-color: #FFD166;
;
}
.slider-btn-prew,
.slider-btn-next {
  width: 16px;
  height: 16px;
  background-color: transparent;
  background-image: url('~assets/icons/icon_arrow.svg');
  background-repeat: no-repeat;
  background-position: center;
  border: none;
  cursor: pointer;
}
.slider-btn-next {
  transform: rotateY(180deg);
}

.registration-form {
  width: 385px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: var(--gray-700);
  border-bottom-right-radius: 25px;
  border-top-right-radius: 25px;
}
.registration-title-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.registration-icon {
  width: 45px;
  height: 45px;
  border-radius: 15px;
  background-color: var(--green);
  background-image: url('~assets/icons/icon_user.svg');
  background-position: center;
  background-repeat: no-repeat;
  margin-bottom: 10px;
}
.registration-form-title {
  font-family: var(--gilroy);
  font-size: 25px;
  font-weight: 700;
  line-height: 25px;
  color: #fff;
  margin-bottom: 25px;
}
.fieldset-box {
  position: relative;
  display: flex;
  flex-direction: column;
}
.password-error, .check-password-error {
  display: none;
font-family: var(--poppins);
color: var(--orange);
font-size: 10px;
font-weight: 400;
line-height: 12px;
margin: -5px 0 10px 0;
padding-left: 16px;
}
.no-error {
  display: block;
}

.choose-messenger {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-bottom: 15px;
  padding-top: 15px;
}
.messenger-tilte {
  font-family: var(--roboto);
  font-size: 12px;
  font-weight: 700;
  line-height: 12px;
  color: var(--gray-400);
  text-transform: uppercase;
  margin-bottom: 10px;
}

.communication-method {
  display: flex;
  width: 295px;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.btn-submit-reg-form {
  padding: 12px 16px;
  border-radius: 90px;
  font-family: var(--gilroy);
  font-weight: 700;
  line-height: 16px;
  cursor: pointer;
  background-color: var(--yellow);
  color: var(--gray-800);
  border: none;
  transition: background-color 300ms ease;
  margin: 0 auto;
}
.btn-submit-reg-form:hover {
  background-color: rgba(255, 199, 55, 0.75);
}

@media (min-width: 375px) and (max-width: 767px) {
  .registration-slider {
    display: none;
  }
  .registration-form {
    max-width: 355px;
    border-radius: 25px;
  }
  .registration-title-wrapper {
    flex-direction: row;
    gap: 10px;
    align-self: flex-start;
  }

  .registration-icon {
    margin-bottom: 25px;
  }
}
</style>
