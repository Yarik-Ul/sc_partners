<template>
  <div class="container">
    <Login />
    <Registration />
    <TheHeader />
    <TheMain />
  </div>
</template>

<style>
.container {
  max-width: 1440px;
  background-color: var(--gray-800);
  background-image: url('~assets/img/main_bg.png');
  background-position: center bottom;
  background-repeat: no-repeat;
  background-size: contain;
  margin: 0 auto;
  font-family: var(--roboto);
  font-size: 14px;
  line-height: 24px;
  font-weight: 400;
  color: var(--gray-500);
  position: relative;
}
.active {
  display: flex;
}
@media (min-width: 375px) and (max-width: 767px) {
  .container {
    background-image: url('~assets/img/bg_mini.png');
    background-size: 100%;
    background-position: top;
  }
}
</style>

<script>
export default {
  name: 'IndexPage',
  mounted() {
    // ***** opening the registration and login window *****
    const header = document.querySelector('.header-container') // main container
    const btnLogin = document.querySelector('.btn-login') // login button
    const btnReg = document.querySelector('.btn-reg') // registration button
    const loginWindow = document.querySelector('.login-form-container') // login window
    const regWindow = document.querySelector('.registration-container') // registration window
    const closeForm = document.querySelectorAll('.close-form') //button close form

    function showRegLoginWindow(event) {
      if (event.target === btnLogin) {
        loginWindow.classList.add('active')
      } else if (event.target === btnReg) {
        regWindow.classList.add('active')
      }
    }

    header.addEventListener('click', showRegLoginWindow)

    //closing the registration and login window
    closeForm.forEach((elem) => {
      elem.onclick = () => {
        regWindow.classList.remove('active')
        loginWindow.classList.remove('active')
        clearInputs()
      }
    })
    const iconSpans = document.querySelectorAll('span[class*="icon"]') //all span with class containing "icon"
    const allInputs = document.querySelectorAll('input:not([type="radio"])') //all inputs
    const allerrorText = document.querySelectorAll('p[class*="error"]') //all p with class containing "error"
    // clear inputs
    function clearInputs() {
      allInputs.forEach((elem) => {
        elem.value = ''
        elem.style.borderColor = "var(--gray-500)";
      })
      iconSpans.forEach((elem) => elem.classList.remove('valid', 'unvalid'))
      allerrorText.forEach((elem) => elem.classList.remove('error'))
    }

    // ***** END opening the registration and login window *****

    // ***** slider in registration *****

    const sliderContainer = document.querySelector('.reg-slider-wrap') // container with slider elements
    const sliderElements = document.querySelectorAll('.slider-element') // all slider elements
    const paginationDots = document.querySelectorAll('.pagination-dot') // sliders pagination
    let currentIndex = 0 // slider element index

    function showSlide(index) {
      currentIndex = index
      let elemWidth = -index * sliderElements[0].offsetWidth
      sliderContainer.style.transform = `translateX(${elemWidth}px)`
      pagination()
    }

    function pagination() {
      paginationDots.forEach((dot, index) => {
        index === currentIndex
          ? dot.classList.add('dot-active')
          : dot.classList.remove('dot-active')
      })
    }
    // Start with first slide
    pagination()

    //pagination navigation
    paginationDots.forEach((dot, index) => {
      dot.addEventListener('click', () => {
        showSlide(index)
      })
    })

    // next slide
    document.querySelector('.slider-btn-next').addEventListener('click', () => {
      if (currentIndex < sliderElements.length - 1) {
        showSlide(currentIndex + 1)
      }
    })

    // prev slide
    document.querySelector('.slider-btn-prew').addEventListener('click', () => {
      if (currentIndex > 0) {
        showSlide(currentIndex - 1)
      }
    })

    // ***** END slider in registration *****

    // ***** Change the text of placeholders in messengers *****

    const radioBtns = document.querySelectorAll('input[type="radio"]') //radio buttons
    const inputElem = document.getElementById('messenger-link') // input with placeholder

    radioBtns.forEach((btn) => {
      btn.addEventListener('change', function () {
        if (btn.value === 'telegram') {
          inputElem.placeholder = '@телеграм_адреса'
        } else if (btn.value === 'skype') {
          inputElem.placeholder = 'skype'
        }
      })
    })
    // ***** END change the text of placeholders in messengers *****

    // ***** Show password *****
    const showPasswordBtn = document.querySelectorAll('.show-password') // all btn show password
    const passwordInput = document.querySelectorAll('input[type="password"]') // all input with type password

    showPasswordBtn.forEach((btn) => {
      btn.onclick = () => {
        passwordInput.forEach((elem) => {
          elem.type === 'password'
            ? (elem.type = 'text')
            : (elem.type = 'password')
        })
      }
    })
    // ***** END Show password *****

    // ***** Validation for inputs *****
    // validate function
    function validateInputs(inputElem, iconElem, pattern) {
      let isValid = pattern.test(inputElem.value)

      isValid
        ? (inputElem.style.borderColor = 'var(--green)')
        : (inputElem.style.borderColor = 'var(--orange)')

      iconElem.classList.toggle('valid', isValid)
      iconElem.classList.toggle('unvalid', !isValid)

      return isValid
    }

    //Check login
    const loginName = document.getElementById('login-name') // input login (email)
    const validateIconLog = document.querySelector('.login-icon') // validation icon
    const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/ //email pattern

    loginName.addEventListener('input', () => {
      validateInputs(loginName, validateIconLog, emailPattern)
    })

    // check password
    const loginPassword = document.getElementById('login-password') // input password
    let inputValid //flag

    loginPassword.addEventListener('input', () => {
      if (loginPassword.value.length >= 6 && loginPassword.value.length <= 16) {
        inputValid = true
      } else {
        inputValid = false
      }
    })

    // check name
    const userName = document.getElementById('name') // input name
    const validateIconName = document.querySelector('.name-icon') // validation icon
    const namePattern = /^[а-яА-ЯїЇєЄіІґҐ]{2,16}$/ // name pattern

    userName.addEventListener('input', () => {
      validateInputs(userName, validateIconName, namePattern)
    })

    // check email
    const userEmail = document.getElementById('email') //input email
    const validateIconEmail = document.querySelector('.email-icon') // validation icon

    userEmail.addEventListener('input', () => {
      validateInputs(userEmail, validateIconEmail, emailPattern)
    })

    // check password for registration
    const userPassword = document.getElementById('password') // input password
    const checkUserPassword = document.getElementById('check-password') // input check password
    const passwordError = document.querySelector('.password-error') // password error text
    const checkPasswordError = document.querySelector('.check-password-error') // check password error text
    const passwordPattern = /^(?=.*[a-zA-Z])(?=.*\d)[a-zA-Z\d_-]{6,16}$/ // password pattern

    userPassword.addEventListener('input', () => {
      let isValid = passwordPattern.test(userPassword.value)
      if (isValid) {
        userPassword.style.borderColor = 'var(--green)'
        passwordError.classList.remove('error')
      } else {
        userPassword.style.borderColor = 'var(--orange)'
        passwordError.classList.add('error')
      }
    })

    checkUserPassword.addEventListener('input', () => {
      if (checkUserPassword.value === userPassword.value) {
        checkUserPassword.style.borderColor = 'var(--green)'
        checkPasswordError.classList.remove('error')
      } else {
        checkUserPassword.style.borderColor = 'var(--orange)'
        checkPasswordError.classList.add('error')
      }
    })
    // check messenger
    const messenger = document.getElementById('messenger-link') // input messenger
    const validateIconMessenger = document.querySelector('.messenger-icon') // validation icon
    const messengerPattern = /^@[a-zA-Z\d]{2,}$/ // messenger pattern

    messenger.addEventListener('input', () => {
      validateInputs(messenger, validateIconMessenger, messengerPattern)
    })
  },
}
</script>
