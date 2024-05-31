<script>
export default {
  props: {
    loginActive: {
      type: Boolean,
    }
  },
  data() {
    return {
      loginEmail: '',
      loginPassword: '',
      emailPattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      password: 'password',
      isValidEmail: false,
      passwordText: true,
    }
  },
  computed: {
    classObjEmail() {
      if (this.loginEmail !== '') {
        return this.isValidEmail ? 'valid' : 'unvalid';
      }
    },
  },
  methods: {
    closeForm() {
      this.$emit('closeForm')
    },
    clearInput() {
      this.loginEmail = ''
    },
    showPassword() {
      this.password = (this.password === 'password') ? 'text' : 'password';
      this.passwordText = !this.passwordText;
    },

    validateFunction(pattern, inputElement) {
      return pattern.test(inputElement);
    },
    validateLoginEmail() {
      this.isValidEmail = this.validateFunction(this.emailPattern, this.loginEmail);
    }
  },
}
</script>

<template>
  <div class="login-form-container" :class="{ 'active': loginActive }">
    <div class="login-form-wrapper">
      <div class="close-form" @click="closeForm">
        <span class="close-line"></span>
      </div>
      <div class="login-title-wrapper">
        <div class="icon-login"></div>
        <p class="login-title">Вхід</p>
      </div>
      <form class="login-form" action="#" method="post">
        <fieldset class="fieldset-login-form">
          <div class="input-wrapper">
            <input class="input-style" :class="classObjEmail" @input="validateLoginEmail" v-model="loginEmail"
              type="email" name="loginEmail" placeholder="Ваш email" />
            <button class="validate-btn" :class="classObjEmail" @click.prevent="clearInput"></button>
          </div>
          <div class="input-wrapper">
            <input class="input-style" :class="{ 'password-text': passwordText }" v-model="loginPassword" :type="password"
              name="loginPassword" placeholder="Ваш пароль" />
            <button @click.prevent="showPassword" class="show-password"></button>
          </div>
          <button class="login-submit-btn" @submit.prevent type="submit">Війти</button>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<style>
.login-form-container {
  position: fixed;
  z-index: 100;
  overflow-y: auto;
  display: none;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  background-color: rgb(53 57 69 / 90%);
}

.login-form-wrapper {
  position: relative;
  max-width: 355px;
  padding: 25px 30px;
  background-color: var(--gray-700);
  border-radius: 25px;
}

.close-form {
  position: absolute;
  top: 10px;
  right: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  cursor: pointer;
  background-color: var(--gray-600);
  border-radius: 50%;
}

.close-line {
  position: relative;
  display: block;
  width: 14px;
  height: 14px;
}

.close-line::before,
.close-line::after {
  position: absolute;
  top: 6px;
  left: -3px;
  width: 20px;
  height: 2px;
  content: '';
  background-color: var(--gray-500);
  border-radius: 1px;
  transform: rotateZ(45deg);
}

.close-line::after {
  transform: rotateZ(-45deg);
}

.login-title-wrapper {
  display: flex;
  align-items: center;
  margin-bottom: 25px;
}

.icon-login {
  position: relative;
  width: 45px;
  height: 45px;
  padding: 10px;
  margin-right: 10px;
  background-color: var(--orange);
  background-image: url('~assets/icons/icon_lock.svg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: 25px;
  border-radius: 15px;
}

.login-title {
  font-family: var(--gilroy);
  font-size: 25px;
  font-weight: 700;
  line-height: 25px;
  color: #fff;
  text-align: left;
}

.fieldset-login-form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.login-submit-btn {
  padding: 16px 24px;
  font-family: var(--gilroy);
  font-size: 16px;
  font-weight: 700;
  line-height: 16px;
  cursor: pointer;
  background-color: var(--yellow);
  border: none;
  border-radius: 90px;
  transition: background-color 300ms ease;
}

.login-submit-btn:hover {
  background-color: rgb(255 199 55 / 75%);
}

@media (width >=375px) and (width <=767px) {
  .login-form-wrapper {
    position: fixed;
    bottom: 10px;
  }
}
</style>
