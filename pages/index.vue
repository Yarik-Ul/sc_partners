<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      regActive: false,
      loginActive: false,
      loginPassword: '',
    }
  },
  methods: {
    showLoginWindow() {
      this.loginActive = true
      document.body.style.overflow = "hidden"
    },

    showRegWindow() {
      this.regActive = true
      document.body.style.overflow = "hidden"
    },

    closeForm() {
      this.regActive = false
      this.loginActive = false
      this.loginPassword = '',
      document.body.style.overflow = ""
    }
  },
}
</script>
<template>
  <div class="container">
    <Login :loginActive="loginActive" :loginPassword="loginPassword" @closeForm="closeForm" />
    <Registration :regActive="regActive" @closeForm="closeForm" />
    <TheHeader @showLoginWindow="showLoginWindow" @showRegWindow="showRegWindow" />
    <TheMain />
  </div>
</template>

<style>
body {
  width: 100%;
  min-height: 100vh;
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

@media (width >=375px) and (width <=767px) {
  body {
    background-image: url('./assets/img/bg_mini.webp');
  }
}
</style>