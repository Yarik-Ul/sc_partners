<script>
export default {
  props: {
    regActive: {
      type: Boolean,
    },
  },
  data() {
    return {
      userName: '',
      regEmail: '',
      registrationPassword: '',
      repeatPassword: '',
      messengerLink: '',
      selectedMessenger: 'telegram',
      mesengerPlaceholder: '@телеграм_адреса',
      isValidName: false,
      isInvalidName: false,
      isValid: false,
      isInvalid: false,
      isValidPass: false,
      isInvalidPass: false,
      isValidCheckPass: false,
      isInvalidCheckPass: false,
      isTelegram: true,
      isSkype: false,
      isValidMsg: false,
      isInvalidMsg: false,
      password: 'password',
      passwordPattern: /^(?=.*[a-zA-Z])(?=.*\d)[a-zA-Z\d_-]{6,16}$/,
      userNamePattern: /^[а-яА-ЯїЇєЄіІґҐ]{2,16}$/,
      emailPattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      messengerPattern: /^@[a-zA-Z\d]{2,}$/,
    }
  },
  methods: {
    closeForm() {
      this.$emit('closeForm')
    },

    validationPattern(pattern, inputElement) {
      return pattern.test(inputElement);
    },

    validateUserName() {
      this.isValidName = this.validationPattern(this.userNamePattern, this.userName);
      this.isInvalidName = !this.isValidName;
    },

    validateRegEmail() {
      this.isValid = this.validationPattern(this.emailPattern, this.regEmail);
      this.isInvalid = !this.isValid;
    },

    validateRegPass() {
      this.isValidPass = this.validationPattern(this.passwordPattern, this.registrationPassword);
      this.isInvalidPass = !this.isValidPass;
    },

    checkPassword() {
      if (this.registrationPassword === this.repeatPassword) {
        this.isValidCheckPass = true
        this.isInvalidCheckPass = false
      } else if (this.registrationPassword !== this.repeatPassword) {
        this.isInvalidCheckPass = true
        this.isValidCheckPass = false
      }
    },

    validateMessenger() {
      this.isValidMsg = this.validationPattern(this.messengerPattern, this.messengerLink);
      this.isInvalidMsg = !this.isValidMsg;
    },

    showPassword() {
      this.password === 'password'
        ? (this.password = 'text')
        : (this.password = 'password')
    },
    clearInputName() {
      this.userName = ''
    },
    clearInputEmail() {
      this.regEmail = ''
    },
    chooseTelegram() {
      this.isTelegram = !this.isTelegram
      this.isSkype = !this.isSkype
      if (this.isTelegram) {
        this.selectedMessenger = 'telegram'
        this.mesengerPlaceholder = '@телеграм_адреса'
      } else {
        this.selectedMessenger = 'skype'
        this.mesengerPlaceholder = 'Skype'
      }
    },
    chooseSkype() {
      this.isSkype = !this.isSkype
      this.isTelegram = !this.isTelegram
      if (this.isTelegram) {
        this.selectedMessenger = 'telegram'
        this.mesengerPlaceholder = '@телеграм_адреса'
      } else {
        this.selectedMessenger = 'skype'
        this.mesengerPlaceholder = 'Skype'
      }
    },
  },
}
</script>

<template>
  <div class="registration-container" :class="{ active: regActive }">
    <div class="registration-wrapper">
      <div @click="closeForm" class="close-form">
        <span class="close-line"></span>
      </div>
      <Slider />
      <div class="registration-form">
        <div class="registration-title-wrapper">
          <div class="registration-icon"></div>
          <p class="registration-form-title">Реєстрація</p>
        </div>
        <form action="#" method="post">
          <fieldset class="fieldset-box">
            <div>
              <input v-model="userName" @input="validateUserName"
                :class="{ 'input-error': isInvalidName, 'input-not-error': isValidName, }" class="input-style" type="text"
                name="name" id="name" placeholder="Ваше імʼя" />
              <label for="name">
                <span @click="clearInputName" :class="{ valid: isValidName, unvalid: isInvalidName }">
                </span>
              </label>
            </div>
            <div>
              <input :class="{ 'input-error': isInvalid, 'input-not-error': isValid }" v-model="regEmail"
                @input="validateRegEmail" class="input-style" type="email" name="email" id="email"
                placeholder="Ваш email" />
              <label for="email"><span @click="clearInputEmail"
                  :class="{ valid: isValid, unvalid: isInvalid }"></span></label>
            </div>
            <div>
              <input v-model="registrationPassword" :class="{
                'input-error': isInvalidPass,
                'input-not-error': isValidPass,
              }" @input="validateRegPass" class="input-style" :type="password" name="password" id="password"
                placeholder="Ваш пароль" />
              <label for="password">
                <p v-if="isInvalidPass" class="password-error">
                  Пароль має містити літери і символи
                </p>
                <span @click="showPassword" class="show-password"></span>
              </label>
            </div>
            <div>
              <input v-model="repeatPassword" @input="checkPassword" :class="{
                'input-error': isInvalidCheckPass,
                'input-not-error': isValidCheckPass,
              }" class="input-style" :type="password" name="check-password" id="check-password"
                placeholder="Повторіть пароль" />
              <label for="check-password">
                <p v-if="isInvalidCheckPass" class="check-password-error">
                  Паролі не співпадають
                </p>
                <span @click="showPassword" class="show-password"></span>
              </label>
            </div>
            <div class="choose-messenger">
              <p class="messenger-tilte">Оберіть спосіб звязку</p>
              <div class="communication-method">
                <button @click.prevent="chooseTelegram" class="telegram" :class="{ 'choose-msg': isTelegram }"></button>
                <button @click.prevent="chooseSkype" class="skype" :class="{ 'choose-msg': isSkype }"></button>
                <input :class="{
                  'input-error': isInvalidMsg,
                  'input-not-error': isValidMsg,
                }" v-model="messengerLink" @input="validateMessenger" type="text" id="messenger-link"
                  name="messenger-link" class="input-style messenger-input" :placeholder="mesengerPlaceholder" />
                <label for="messenger-link"><span :class="{ valid: isValidMsg, unvalid: isInvalidMsg }"
                    class="messenger-icon"></span></label>
              </div>
            </div>
            <button @click.prevent="" type="submit" class="btn-submit-reg-form">
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
  z-index: 10;
  display: none;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  background-color: rgb(53 57 69 / 90%);
}

.registration-wrapper {
  position: relative;
  display: flex;
  max-width: 770px;
  border-radius: 25px;
}

.registration-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 385px;
  padding: 60px 45px 45px;
  background-color: var(--gray-700);
  border-top-right-radius: 25px;
  border-bottom-right-radius: 25px;
}

.registration-title-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.registration-icon {
  width: 45px;
  height: 45px;
  margin-bottom: 10px;
  background-color: var(--green);
  background-image: url('~assets/icons/icon_user.svg');
  background-repeat: no-repeat;
  background-position: center;
  border-radius: 15px;
}

.registration-form-title {
  margin-bottom: 25px;
  font-family: var(--gilroy);
  font-size: 25px;
  font-weight: 700;
  line-height: 25px;
  color: #fff;
}

.fieldset-box {
  position: relative;
  display: flex;
  flex-direction: column;
}

.password-error,
.check-password-error {
  padding-left: 16px;
  margin: -5px 0 10px;
  font-family: var(--poppins);
  font-size: 10px;
  font-weight: 400;
  line-height: 12px;
  color: var(--orange);
}

.choose-messenger {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding-top: 15px;
  padding-bottom: 15px;
}

.messenger-tilte {
  margin-bottom: 10px;
  font-family: var(--roboto);
  font-size: 12px;
  font-weight: 700;
  line-height: 12px;
  color: var(--gray-400);
  text-transform: uppercase;
}

.communication-method {
  display: flex;
  gap: 10px;
  align-items: center;
  justify-content: space-between;
  width: 295px;
}

.btn-submit-reg-form {
  padding: 12px 16px;
  margin: 0 auto;
  font-family: var(--gilroy);
  font-weight: 700;
  line-height: 16px;
  color: var(--gray-800);
  cursor: pointer;
  background-color: var(--yellow);
  border: none;
  border-radius: 90px;
  transition: background-color 300ms ease;
}

.btn-submit-reg-form:hover {
  background-color: rgb(255 199 55 / 75%);
}

@media (width >=375px) and (width <=767px) {
  .registration-wrapper {
    position: fixed;
    bottom: 10px;
  }

  .registration-form {
    max-width: 355px;
    padding: 25px 30px;
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
