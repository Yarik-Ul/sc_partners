<script>
export default {
  data() {
    return{
      
    }

  },
  methods: {
    showLoginWindow(){
      this.$emit('showLoginWindow')
    },
    showRegWindow(){
      this.$emit('showRegWindow')
    }
  },
}
</script>
<template>
  <header class="header">
    <div class="header-container">
      <div class="logo-wrapper">
        <a href="#"><img src="~assets/icons/logo.svg" alt="logo" /></a>
      </div>
      <div class="header-btn">
        <button @click="showLoginWindow" class="btn-login">Вхід</button>
        <button @click="showRegWindow" class="btn-reg">Реєстрація</button>
      </div>
    </div>
  </header>
</template>

<style>
.header-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  place-items: center center;
  max-width: 1440px;
  padding: 24px 0;
  margin: 0 auto 100px;
  border-bottom: 1px solid var(--gray-700);

}

.logo-wrapper {
  grid-column: 2/3;
}

.logo-wrapper img {
  vertical-align: middle;
}

.header-btn {
  display: flex;
  grid-column: 3/4;
  justify-self: end;
  margin-right: 24px;
}

.btn-login,
.btn-reg {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 40px;
  font-family: var(--gilroy);
  font-weight: 700;
  line-height: 16px;
  color: var(--gray-100);
  cursor: pointer;
  background-color: transparent;
  border: 2px solid var(--gray-500);
  border-radius: 90px;
  transition: background-color 300ms ease;
}

.btn-reg {
  width: 106px;
  height: 40px;
  margin-left: 15px;
  color: var(--gray-800);
  background-color: var(--yellow);
  border: none;
}

.btn-reg:hover {
  background-color: rgb(255 199 55 / 75%);
}

.btn-login:hover {
  color: var(--gray-700);
  background-color: var(--gray-100);
  border: 2px solid var(--gray-100);
}

@media (width >= 375px) and (width <= 767px) {
  .header {
    position: sticky;
    top: 0;
    z-index: 5;
    background-color: var(--gray-800);
  }

  .header-container {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    padding: 10px 15px;
    margin-bottom: 50px;
  }

  .logo-wrapper {
  grid-column: 1/2;
  justify-self: start;
}

.header-btn {
  grid-column: 2/3;
  margin-right: 0;
}
 
  .btn-reg {
    margin-left: 10px;
  }
}
</style>
