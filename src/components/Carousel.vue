<script setup>

import {computed, ref} from "vue";

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
  index: {
    type: Number,
    default: 0,
  }
})

const emit = defineEmits(['change-index']);

const sliderItems = ref(null);

const sliderItemsStyle = computed(() => {
  const containerWidth = sliderItems.value?.clientWidth || 0;
  return `transform: translateX(-${props.index * containerWidth}px);`//
})

</script>

<template>
  <div class="slider">
    <div class="slider__container">
      <ul
          ref="sliderItems"
          class="slider-items"
          :style="sliderItemsStyle"
      >
        <li v-for="item in props.items">
          <slot :item="item"></slot>
        </li>
      </ul>

      <div
          class="slider-control slider-control_left"
          @click="emit('change-index', props.index - 1)"
      >
        <img src="../../public/arrow-left.png" alt="arrow" />
      </div>
      <div
          class="slider-control slider-control_right"
          @click="emit('change-index', props.index + 1)"
      >
        <img src="../../public/arrow-left.png" alt="arrow" />
      </div>

      <div class="slider-count">
        {{props.index + 1}}/{{props.items.length}}
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
