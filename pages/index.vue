<script>
export default {
  name: 'IndexPage',

  data() {
    return {
      user: {
        loginEmail: '',
        loginPassword: '',
      },

      newUser: {
        userName: '',
        regEmail: '',
        regPass: '',
        messengerLink: '',
      },

      repeatRegPass: '',
      regActive: false,
      loginActive: false,
    }
  },

  methods: {
    showLoginWindow() {
      this.loginActive = true;
      document.body.classList.toggle('scroll-off');
    },

    showRegWindow() {
      this.regActive = true;
      document.body.classList.toggle('scroll-off');
    },

    closeForm() {
      this.regActive = false;
      this.loginActive = false;
      document.body.classList.toggle('scroll-off');
      this.repeatRegPass = '',
      this.newUser = {
        userName: '',
        regEmail: '',
        regPass: '',
        messengerLink: '',
      },
      this.user = {
        loginEmail: '',
        loginPassword: '',
      }
    },

  },
}
</script>

<template>
  <div class="container">
    <Login :loginActive="loginActive" @closeForm="closeForm" :user="user"/>
    <Registration :regActive="regActive" @closeForm="closeForm" :newUser="newUser" :repeatRegPass="repeatRegPass"/>
    <TheHeader @showLoginWindow="showLoginWindow" @showRegWindow="showRegWindow" />
    <TheMain />
  </div>
</template>

<style>
body {
  width: 100%;
  background-color: var(--gray-800);
  background-image: url('./assets/img/bg.webp');
  background-repeat: no-repeat;
  background-position-x: center;
  background-position-y: top;
  background-size: cover;
}

.container {
  width: 100%;
  font-family: var(--roboto);
  font-size: 14px;
  font-weight: 400;
  line-height: 24px;
  color: var(--gray-500);
}

.active {
  display: flex;
}

.scroll-off {
  overflow: hidden;
}

@media (width >=375px) and (width <=767px) {
  body {
    background-image: url('./assets/img/bg_mini.webp');
  }
}
</style>