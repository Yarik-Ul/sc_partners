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
      greetingUser: '',
      userIsLogged: false,
      userRegistered: false,
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

    hideLoginBtn() {
      this.userIsLogged = true;
      this.greetingUser = this.user.loginEmail;
    },
    userLogOut() {
      this.userIsLogged = false;
    },
  },

}
</script>

<template>
  <div class="container">
    <Login  
      @closeForm="closeForm" 
      @hideLoginBtn="hideLoginBtn"
      :loginActive="loginActive" 
      :user="user"
      :userIsLogged="userIsLogged" />
    <Registration 
      @closeForm="closeForm" 
      :regActive="regActive"
      :userRegistered="userRegistered" 
      :newUser="newUser" />
    <TheHeader 
      @showLoginWindow="showLoginWindow" 
      @showRegWindow="showRegWindow" 
      @userLogOut="userLogOut"
      :userIsLogged="userIsLogged" 
      :greetingUser="greetingUser" />
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