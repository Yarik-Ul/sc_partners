<script>
export default {
  data() {
    return {
      //for practice
      slides: [
        { cpa: "$25", revshare: '60%' },
        { cpa: "$30", revshare: '50%' },
        { cpa: "$20", revshare: '65%' }
      ],

      currentIndex: 0,
      currentPagination: 0,
    }
  },

  methods: {
    showSlide() {
      this.$refs.carousel.style.transform = `translateX(-${this.currentIndex * 220}px)`
    },

    nextSlide() {
      if (this.currentIndex < this.slides.length - 1) {
        this.currentIndex++
        this.currentPagination++
        this.showSlide()
      }
    },

    prevSlide() {
      if (this.currentIndex > 0) {
        this.currentIndex--
        this.currentPagination--
        this.showSlide()
      }
    },

    paginationNavigation(index) {
      this.currentIndex = index;
      this.showSlide()
    }
  }

}
</script>
<template>
  <div class="registration-slider">
    <h3 class="slider-title">Зможеш обрати <br /> свій варіант</h3>
    <div class="reg-slider-container">
      <div class="reg-slider-wrap" ref="carousel">
        <div class="slider-element" v-for="(slide, index) in slides" :key="index">
          <ul class="slider-list">
            <li class="slider-list-item">
              <div class="list-item-icon"></div>
              <div class="list-item-text">
                <h4 class="list-item-title">CPA</h4>
                <p class="list-item-disc">{{ slide.cpa }} і вище</p>
              </div>
            </li>
            <li class="slider-list-item">
              <div class="list-item-icon"></div>
              <div class="list-item-text">
                <h4 class="list-item-title">REVSHARE</h4>
                <p class="list-item-disc">Піднімай до {{ slide.revshare }}</p>
              </div>
            </li>
            <li class="slider-list-item">
              <div class="list-item-icon"></div>
              <div class="list-item-text">
                <h4 class="list-item-title">Гібрід</h4>
                <p class="list-item-disc">Зробимо як скажеш</p>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="slider-pagination-wrap">
      <button class="slider-btn-prew slider-btn" @click="prevSlide"></button>
      <div class="pagination-dots">
        <span class="pagination-dot" @click="paginationNavigation(index)" :class="{ 'dot-active': currentIndex == index }"
          v-for="(dot, index) in slides.length" :key="index"></span>
      </div>
      <button class="slider-btn-next slider-btn" @click="nextSlide"></button>
    </div>
  </div>
</template>

<style>
.registration-slider {
  width: 385px;
  background-color: var(--green);
  background-image: url('~assets/img/slider_bg.webp');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  border-top-left-radius: 25px;
  border-bottom-left-radius: 25px;
}

.slider-title {
  margin: 78px 0 65px 56px;
  font-family: var(--roboto);
  font-size: 25px;
  font-weight: 400;
  line-height: 40px;
  color: var(--gray-100);
}

.reg-slider-container {
  position: relative;
  width: 220px;
  height: 185px;
  margin-bottom: 82px;
  margin-left: 54px;
  overflow: hidden;
}

.reg-slider-wrap {
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  transition: 500ms ease;
}

.slider-element {
  width: 220px;
}

.slider-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.slider-list-item {
  display: flex;
}

.list-item-icon {
  position: relative;
  width: 45px;
  height: 45px;
  margin-right: 25px;
  background-color: #fff3;
  border-radius: 50%;
}

.list-item-icon::after {
  position: absolute;
  top: 10px;
  left: 10px;
  width: 24px;
  height: 24px;
  content: '';
  background-image: url('~assets/icons/line.svg');
}

.list-item-title {
  font-family: var(--gilroy);
  font-size: 14px;
  font-weight: 700;
  line-height: 16px;
  color: var(--gray-100);
}

.list-item-disc {
  font-family: var(--roboto);
  font-size: 14px;
  font-weight: 400;
  line-height: 24px;
  color: var(--gray-100);
}

.slider-pagination-wrap {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 96px;
  margin: 0 auto 108px;
}

.pagination-wrap {
  display: flex;
}

.pagination-dots {
  display: flex;
  gap: 10px;
  align-items: center;
  justify-content: space-between;
}

.pagination-dot {
  display: block;
  width: 8px;
  height: 8px;
  cursor: pointer;
  background-color: #fff;
  border-radius: 50%;
}

.dot-active {
  background-color: #ffd166;
}

.slider-btn-prew,
.slider-btn-next {
  width: 16px;
  height: 16px;
  cursor: pointer;
  background-color: transparent;
  background-image: url('~assets/icons/icon_arrow.svg');
  background-repeat: no-repeat;
  background-position: center;
  border: none;
}

.slider-btn-next {
  transform: rotateY(180deg);
}

@media (width >=768px) and (width <=1023px) {
  .registration-slider {
    width: 360px;
  }
}

@media (width >=375px) and (width <=767px) {
  .registration-slider {
    display: none;
  }
}
</style>