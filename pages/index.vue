<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      regActive: false,
      loginActive: false,
    }
  },
  methods: {
    showLoginWindow() {
      this.loginActive = true
      document.body.classList.toggle('scroll-off')
    },

    showRegWindow() {
      this.regActive = true
      document.body.classList.toggle('scroll-off')
    },

    closeForm() {
      this.regActive = false
      this.loginActive = false
      this.loginPassword = '',
      document.body.classList.toggle('scroll-off')
    }
  },
}
</script>
<template>
  <div class="container">
    <Login :loginActive="loginActive" @closeForm="closeForm" />
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
.scroll-off {
  overflow: hidden;
}

@media (width >=375px) and (width <=767px) {
  body {
    background-image: url('./assets/img/bg_mini.webp');
  }
}
</style>