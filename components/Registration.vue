<script>
export default {
  props: {
    regActive: {
      type: Boolean,
    },

    newUser: {
      type: Object,
    },
  },

  data() {
    return {
      messengerPlaceholder: '@телеграм_адреса',
      isValidName: false,
      isValidEmail: false,
      isValidPass: false,
      isValidCheckPass: true,
      isTelegram: true,
      isSkype: false,
      isValidMsg: false,
      passwordText: true,
      userRegistered: false,
      repeatRegPass: '',
      password: 'password',
      passwordPattern: /^(?=.*[a-zA-Z])(?=.*\d)[a-zA-Z\d_-]{6,16}$/,
      userNamePattern: /^[а-яА-ЯїЇєЄіІґҐ]{2,16}$/,
      emailPattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      messengerPattern: /^@[a-zA-Z\d]{2,}$/,
    }
  },

  computed: {
    classObjName() {
      if (this.newUser.userName !== '') {
        this.isValidName = this.validationPattern(this.userNamePattern, this.newUser.userName);
        return this.isValidName ? 'valid' : 'unvalid';
      }
    },

    classObjEmail() {
      if (this.newUser.regEmail !== '') {
        this.isValidEmail = this.validationPattern(this.emailPattern, this.newUser.regEmail);
        return this.isValidEmail ? 'valid' : 'unvalid';
      }
    },

    classObjPass() {
      if (this.newUser.regPass !== '') {
        this.isValidPass = this.validationPattern(this.passwordPattern, this.newUser.regPass);
        return this.isValidPass ? 'valid' : 'unvalid';
      }
    },

    classObjRepPass() {
      if (this.repeatRegPass !== '') {
        this.isValidCheckPass = this.newUser.regPass === this.repeatRegPass;
        return this.isValidCheckPass ? 'valid' : 'unvalid';
      }
    },

    classObjMsg() {
      if (this.newUser.messengerLink !== '') {
        this.isValidMsg = this.validationPattern(this.messengerPattern, this.newUser.messengerLink);
        return this.isValidMsg ? 'valid' : 'unvalid';
      }
    }
  },

  methods: {
    validationPattern(pattern, inputElement) {
      return pattern.test(inputElement);
    },
    
    closeForm() {
      this.repeatRegPass = '',
        this.$emit('closeForm');
    },

    async toRegister() {
      if (this.isValidName && this.isValidEmail && this.isValidPass && this.isValidCheckPass && this.isValidMsg) {
        try {
          await fetch('#', {
            method: 'POST',
            body: JSON.stringify(this.newUser),
          });
          this.userRegistered = true;
          setTimeout(() => {
            this.userRegistered = false;
            this.isValidName = false,
            this.isValidEmail = false,
            this.isValidPass = false,
            this.isValidCheckPass = false,
            this.closeForm();
          }, 2500)
        } catch (error) {
          console.log(error);
        }
      }
    },

    showPassword() {
      this.password = (this.password === 'password') ? 'text' : 'password';
      this.passwordText = !this.passwordText;
    },

    clearInput(value) {
      this.newUser[value] = '';
    },

    chooseMessenger(messenger) {
      if (messenger === 'telegram') {
        this.isTelegram = true;
        this.isSkype = false;
        this.messengerPlaceholder = '@телеграм_адреса';
      } else if (messenger === 'skype') {
        this.isSkype = true;
        this.isTelegram = false;
        this.messengerPlaceholder = 'Skype';
      }
    },
  },
}
</script>

<template>
  <div class="registration-container" :class="{ 'active': regActive }">
    <div class="registration-wrapper">
      <div class="close-form" @click="closeForm">
        <span class="close-line"></span>
      </div>
      <RegistrationSlider />
      <div class="registration-form">
        <div class="user-registered" v-if="userRegistered">
          <p class="user-registered-text">Дякуємо за реєстрацію!</p>
        </div>
        <div class="registration-title-wrapper">
          <div class="registration-icon"></div>
          <p class="registration-form-title">Реєстрація</p>
        </div>
        <form action="#" method="post">
          <fieldset class="fieldset-box">
            <div class="input-wrapper">
              <input 
                :class="classObjName" 
                v-model="newUser.userName" 
                type="text" 
                name="name"
                placeholder="Ваше імʼя" />
              <button class="validate-btn" :class="classObjName" @click.prevent="clearInput('userName')"></button>
            </div>
            <div class="input-wrapper">
              <input 
                :class="classObjEmail" 
                v-model="newUser.regEmail" 
                type="email" 
                name="email"
                placeholder="Ваш email" 
                autocomplete="reg-email" />
              <button class="validate-btn" :class="classObjEmail" @click.prevent="clearInput('regEmail')"></button>
            </div>
            <div class="input-wrapper">
              <input 
                :class="[classObjPass, { 'password-text': passwordText }]"
                v-model="newUser.regPass" 
                :type="password" 
                name="password" 
                placeholder="Ваш пароль"
                autocomplete="new-password" />
              <button class="show-password" @click.prevent="showPassword"></button>
            </div>
            <p class="password-error" v-if="!isValidPass && newUser.regPass">Пароль має містити літери і символи</p>
            <div class="input-wrapper">
              <input 
                :class="[classObjRepPass, { 'password-text': passwordText }]"
                v-model="repeatRegPass" 
                :type="password" 
                name="check-password" 
                placeholder="Повторіть пароль"
                autocomplete="new-password" />
              <button class="show-password" @click.prevent="showPassword"></button>
            </div>
            <p class="check-password-error" v-if="!isValidCheckPass && repeatRegPass">Паролі не співпадають</p>
            <div class="choose-messenger">
              <p class="messenger-tilte">Оберіть спосіб звязку</p>
              <div class="communication-method">
                <button class="telegram" :class="{ 'choose-msg': isTelegram }"
                  @click.prevent="chooseMessenger('telegram')"></button>
                <button class="skype" :class="{ 'choose-msg': isSkype }"
                  @click.prevent="chooseMessenger('skype')"></button>
                <input 
                  class="messenger-input" 
                  :class="classObjMsg" 
                  v-model="newUser.messengerLink"
                  type="text" 
                  name="messenger-link" 
                  :placeholder="messengerPlaceholder" />
                <button class="validate-btn" :class="classObjMsg" @click.prevent="clearInput('messengerLink')"></button>
              </div>
            </div>
            <button class="btn-submit-reg-form" @click.prevent="toRegister">
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
  position: fixed;
  z-index: 100;
  display: none;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  overflow-y: auto;
  background-color: rgb(53 57 69 / 90%);
}

.registration-wrapper {
  position: relative;
  display: flex;
  max-width: 770px;
  border-radius: 25px;
}

.user-registered {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 14;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 51%;
  height: 100%;
  background-color: var(--green);
  background-image: url('~assets/img/slider_bg_reg.webp');
  background-repeat: no-repeat;
  background-position: center;
  background-size: 104%;
  border-top-right-radius: 25px;
  border-bottom-right-radius: 25px;
  transform-origin: left;
  animation: reg-animation 400ms linear both;

}

@keyframes reg-animation {
  0% {
    transform: scaleX(0);
  }

  100% {
    transform: scaleX(1);
  }

}

.user-registered-text {
  font-size: 24px;
  color: #fff;
  animation: reg-animation-text 1500ms ease-in-out both;
}

@keyframes reg-animation-text {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
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
  position: relative;
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

@media (width >=768px) and (width <=1023px) {
  .registration-form {
    width: 360px;
  }
}

@media (width >=375px) and (width <=767px) {
  .registration-wrapper {
    position: fixed;
    bottom: 10px;
  }

  .user-registered {
    width: 100%;
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
