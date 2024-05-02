<script>
export default {
  props: {
    loginActive: {
      type: Boolean,
    },
  },
  data() {
    return {
      loginEmail: '',
      loginPassword: '',
      emailPattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      password: 'password',
      isValid: false,
      isInvalid: false,
    }
  },
  methods: {
    closeForm() {
      this.$emit('closeForm')
    },
    clearInput() {
      this.loginEmail = ''
    },
    showPassword() {
      this.password === 'password'
        ? (this.password = 'text')
        : (this.password = 'password')
    },

    validateFunction(pattern, inputElement) {
      return pattern.test(inputElement);
    },
    validateLoginEmail() {
      this.isValid = this.validateFunction(this.emailPattern, this.loginEmail);
      this.isInvalid = !this.isValid;
    }
  },
}
</script>

<template>
  <div class="login-form-container" :class="{ active: loginActive }">
    <div class="login-form-wrapper">
      <div class="close-form" @click="closeForm">
        <span class="close-line"></span>
      </div>
      <div class="login-title-wrapper">
        <div class="icon-login"></div>
        <p class="login-title">Вхід</p>
      </div>
      <form action="#" method="post" class="login-form">
        <fieldset class="fieldset-login-form">
          <div>
            <input :class="{ 'input-error': isInvalid, 'input-not-error': isValid }" v-model="loginEmail"
              @input="validateLoginEmail" class="input-style" type="email" name="loginEmail" id="login-email"
              placeholder="Ваш email" />
            <label for="login-email"><span @click="clearInput"
                :class="{ valid: isValid, unvalid: isInvalid }"></span></label>
          </div>
          <div>
            <input v-model="loginPassword" class="input-style" :type="password" name="loginPassword" id="login-password"
              placeholder="Ваш пароль" />
            <label for="login-password"><span @click="showPassword" class="show-password"></span></label>
          </div>
          <button @click.prevent="" class="login-submit-btn" type="submit">Війти</button>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<style>
.login-form-container {
  position: absolute;
  z-index: 10;
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
  border-radius: 15px;
}

.icon-login::after {
  position: absolute;
  width: 25px;
  height: 25px;
  content: '';
  background-image: url('~assets/icons/icon_lock.svg');
  background-position: center;
  background-size: contain;
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
