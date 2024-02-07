<script setup>
import {computed} from "vue";

const sliderItemsStyle = computed(() => {
  return `transform: translateX(-px);`//
})

</script>

<template>
  <div class="slider">
    <div class="slider__container">
      <ul
          class="slider-items"
          :style="sliderItemsStyle"
      >
        <!-- слайды сюды -->
      </ul>

      <div class="slider-control slider-control_left">
        <img src="../../public/arrow-left.png" alt="arrow" />
      </div>
      <div class="slider-control slider-control_right">
        <img src="../../public/arrow-left.png" alt="arrow" />
      </div>

      <div class="slider-count">
        {{}}/{{}}
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.slider {
  &__container {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    height: 450px;
    width: 800px;
    overflow: hidden;
    border-radius: 8px;
  }
  &-control {
    filter: invert(1) drop-shadow(0 0 2px rgba(0,0,0, .5));
    width: 50px;
    height: 50px;
    cursor: pointer;
    top: 50%;
    transform: translateY(-50%);
    img {
      width: 100%;
      height: 100%;
    }
    &_left {
      left: 8px;
    }
    &_right {
      right: 8px;
      img {
        transform: rotateY(180deg);
      }
    }
  }
  &-control, &-count {
    position: absolute;
    z-index: 5;
  }
  &-count {
    display: inline-block;
    bottom: 8px;
    right: 16px;
    padding: 8px;
    font-size: 20px;
    color: #fff;
    background: rgba(0,0,0,.4);
    border-radius: 8px;
    z-index: 5;
  }
  &-items {
    position: relative;
    display: flex;
    width: 100%;
    height: 100%;
    transition: all ease-in-out .3s;
    li, img {
      min-width: 100%;
      height: 100%;
    }
  }
}
</style>
