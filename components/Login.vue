<template>
  <div class="login-form-container">
    <div class="login-form-wrapper">
      <div class="close-form close-login"><span class="close-line"></span></div>
      <div class="login-title-wrapper">
        <div class="icon-login"></div>
        <p class="login-title">Вхід</p>
      </div>
      <form action="#" method="post" class="login-form">
        <fieldset class="fieldset-login-form">
          <input
            class="input-style"
            type="email"
            name="loginName"
            id="login-name"
            placeholder="Ваш email"
          />
          <label for="login-name"><span class="login-icon"></span></label>
          <input
            class="input-style"
            type="password"
            name="loginPassword"
            id="login-password"
            placeholder="Ваш пароль"
          />
          <label for="login-password"
            ><span class="show-password"></span
          ></label>
          <button class="login-submit-btn" type="submit">Війти</button>
        </fieldset>
      </form>
    </div>
  </div>
</template>

<style>
.login-form-container {
  position: absolute;
  z-index: 5;
  width: 100%;
  height: 100%;
  background-color: rgba(53, 57, 69, 0.9);
  display: none;
  align-items: center;
  justify-content: center;
}

.login-form-wrapper {
  max-width: 355px;
  background-color: var(--gray-700);
  border-radius: 25px;
  padding: 25px 30px;
  position: relative;
}

.close-form {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--gray-600);
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-line {
  display: block;
  width: 14px;
  height: 14px;
  position: relative;
}

.close-line::before,
.close-line::after {
  content: '';
  position: absolute;
  top: 6px;
  left: -3px;
  width: 20px;
  height: 2px;
  background-color: var(--gray-500);
  transform: rotateZ(45deg);
  border-radius: 1px;
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
  background-color: var(--orange);
  border-radius: 15px;
  padding: 10px;
  margin-right: 10px;
}

.icon-login::after {
  content: '';
  position: absolute;
  width: 25px;
  height: 25px;
  background-image: url('~assets/icons/icon_lock.svg');
  background-position: center;
  background-size: contain;
}

.login-title {
  font-family: var(--gilroy);
  color: #fff;
  font-size: 25px;
  font-weight: 700;
  line-height: 25px;
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
  border-radius: 90px;
  background-color: var(--yellow);
  font-family: var(--gilroy);
  font-size: 16px;
  font-weight: 700;
  line-height: 16px;
  border: none;
  cursor: pointer;
  transition: background-color 300ms ease;
}

.login-submit-btn:hover {
  background-color: rgba(255, 199, 55, 0.75);
}
</style>
