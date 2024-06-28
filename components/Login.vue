<script>
export default {
  props: {
    loginActive: {
      type: Boolean,
    },

    user: {
      type: Object,
    },

    userIsLogged: {
      type: Boolean,
    }
  },

  data() {
    return {
      emailPattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/,
      password: 'password',
      isValidEmail: false,
      isValidLogPass: false,
      passwordText: true,
    }
  },

  computed: {
    classObjEmail() {
      if (this.user.loginEmail !== '') {
        this.isValidEmail = this.validateFunction(this.emailPattern, this.user.loginEmail);
        return this.isValidEmail ? 'valid' : 'unvalid';
      }
    },

    classObjLogPass() {
      if (this.user.loginPassword !== '') {
        this.isValidLogPass = this.user.loginPassword.length >= 6;
        return this.isValidLogPass ? 'valid' : 'unvalid';
      }
    }
  },

  methods: {
    closeForm() {
      this.$emit('closeForm');
    },

    clearInput(value) {
      this.user[value] = '';
    },

    showPassword() {
      this.password = (this.password === 'password') ? 'text' : 'password';
      this.passwordText = !this.passwordText;
    },

    validateFunction(pattern, inputElement) {
      return pattern.test(inputElement);
    },

    async toLogIn() {
      if (this.isValidEmail && this.isValidLogPass) {
        try {
          this.$emit('hideLoginBtn')
          await fetch('#', {
            method: 'POST',
            body: JSON.stringify(this.user),
          });
        } catch (error) {
          console.log(error);
        }
      }
    }
  },
}
</script>

<template>
  <div class="login-form-container" :class="{ 'active': loginActive }">
    <div class="login-form-wrapper">
      <div class="login-success-window" v-show="userIsLogged">
        <span class="hour-line"></span>
        <span class="minute-line"></span>
      </div>
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
            <input 
              :class="classObjEmail" 
              v-model="user.loginEmail" 
              type="email" 
              name="loginEmail"
              placeholder="Ваш email" 
              autocomplete="login-email" />
            <button :class="['validate-btn', classObjEmail]" @click.prevent="clearInput('loginEmail')"></button>
          </div>
          <div class="input-wrapper">
            <input 
              :class="[classObjLogPass, { 'password-text': passwordText }]"
              v-model="user.loginPassword" 
              :type="password" 
              name="loginPassword" 
              placeholder="Ваш пароль"
              autocomplete="current-password" />
            <button @click.prevent="showPassword" class="show-password"></button>
          </div>
          <button class="login-submit-btn" @click.prevent="toLogIn">Війти</button>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<style>
.login-form-container {
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

.login-form-wrapper {
  position: relative;
  max-width: 355px;
  padding: 25px 30px;
  background-color: var(--gray-700);
  border-radius: 25px;
}

.login-success-window {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 15;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  background-color: var(--gray-700);
  border-radius: 25px;

}

.hour-line {
  position: absolute;
  top: 50%;
  left: 50%;
  display: block;
  width: 80px;
  height: 16px;
  background-color: var(--green);
  border-radius: 8px;
  transform: rotate(180deg);
  transform-origin: left;
  animation: hour 2s linear 0.3s both;
}

.minute-line {
  position: absolute;
  top: 51%;
  left: 49%;
  display: block;
  width: 120px;
  height: 10px;
  background-color: var(--green);
  border-radius: 5px;
  transform: rotate(270deg);
  transform-origin: left;
  animation: minutes 2s linear 0.3s both;
}

@keyframes minutes {
  0% {
   transform: rotate(270deg);
  
  }

  50% {
    transform: rotate(630deg);
  }
 
   90% {
    transform: rotate(1020deg);
    scale: 1;
  }

  100% {
    transform: rotate(1020deg);
    scale: 1.3;
  }
 
}

@keyframes hour {
  0% {
   transform: rotate(180deg);
  }

  80% {
    transform: rotate(240deg);
    scale: 1;
  }
  
  100% {
    transform: rotate(240deg);
    scale: 1.3;
  }
 
}

.close-form {
  position: absolute;
  top: 10px;
  right: 10px;
  z-index: 15;
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
