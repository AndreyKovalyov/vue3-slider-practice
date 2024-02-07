<script setup>
import Carousel from './components/Carousel.vue'
import {ref} from "vue";

const items = [
  {
    id: 1,
    name: '1',
    src: './1.jpg',
  },
  {
    id: 2,
    name: '2',
    src: './2.webp',
  },
  {
    id: 3,
    name: '3',
    src: './3.jpg',
  },
  {
    id: 4,
    name: '4',
    src: './4.jpg',
  }
]
const index = ref(0);

</script>

<template>
  <main>
    <Carousel
        v-slot="{item}"
        :items="items"
        :index="index"
        @change-index="index = $event"
    >
      <img :src="item.src" :alt="item.name" />
    </Carousel>
  </main>
</template>

<style>
body {
  background: #e1e1e1;
}
</style>
