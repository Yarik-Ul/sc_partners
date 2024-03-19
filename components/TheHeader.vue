<template>
  <header class="header">
    <div class="header-container">
      <a href="#"><img src="~assets/img/logo.svg" alt="logo" /></a>
      <div class="header-btn">
        <button class="btn-login">Вхід</button>
        <button class="btn-reg">Реєстрація</button>
      </div>
    </div>
  </header>
</template>

<style>
.header-container {
  max-width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  padding: 24px 0;
  border-bottom: 1px solid var(--gray-700);
}

.header-btn {
  position: absolute;
  top: 26px;
  right: 24px;
  display: flex;
}
.btn-login,
.btn-reg {
  width: 60px;
  height: 40px;
  background-color: transparent;
  border: 2px solid var(--gray-500);
  border-radius: 90px;
  color: var(--gray-100);
  font-family: var(--gilroy);
  font-weight: 700;
  line-height: 16px;
  cursor: pointer;
  transition: background-color 300ms ease;
}
.btn-reg {
  width: 106px;
  height: 40px;
  margin-left: 15px;
  background-color: var(--yellow);
  color: var(--gray-800);
  border: none;
}

.btn-reg:hover {
  background-color: rgba(255, 199, 55, 0.75);
}
.btn-login:hover {
  background-color: var(--gray-100);
  color: var(--gray-700);
  border: 2px solid var(--gray-100);
}

@media (min-width: 375px) and (max-width: 767px) {
  .header-container {
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    gap: 20px;
  }
  .header-btn {
    position: static;
  }
  .btn-reg {
    margin-left: 10px;
  }
}
</style>
