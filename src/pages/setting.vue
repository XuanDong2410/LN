<template>
  <component :is="updates" :novels="NovelUpdates" :slides-per-view="8" />
  <component :is="updates" :novels="NovelUpdates" :slides-per-view="10" />
  <component :is="updates" :novels="NovelUpdates" :slides-per-view="6" />
</template>
<script lang="ts" setup>
import updates from "../components/updates.vue"
import NovelUpdates from "../data/updates.json"
// Import Swiper styles

// defineProps<{
//   novels: {
//     img: string
//     novel: string
//     chap: string
//     author: string
//     status: string
//     read: string
//     genre: string

//     route: {
//       name: string
//       params: {
//         novel: number
//       }
//     }
//     describe: string
//   }[]
// }>()
</script>

<!-- <template>
  <swiper
    :slides-per-view="3"
    :grid="{
      rows: 2
    }"
    :space-between="10"
    :pagination="{
      clickable: true
    }"
    :modules="[Grid, Pagination]"
    class="mySwiper text-black"
  >
    <swiper-slide v-for="novel in novels">
      <router-link :to="novel.route">
        <q-card class="w-100 h-100">
        <q-img :src="novel.img" class="w-30% absolute-left" :ratio="1" />
        <q-card class="absolute-right w-70% h-100%">
          <q-card-section class="text-start text-16px text-black">
            <q-item-label class="text-h6 mb-2">{{ novel.novel }}</q-item-label>
            <q-item-label class="text-subtitle1 opacity-80 mb-2">
              <span class="text-orange-500 b-orange-300 b p-1">
                {{ novel.genre }}
              </span>
              | {{ novel.read }} lượt đọc
            </q-item-label>
            <q-item-label
              lines="3"
              class="text-subtitle1 text-12px opacity-80 mt-3"
            >
              {{ novel.describe }}
            </q-item-label>
          </q-card-section>
        </q-card>
      </q-card>
      </router-link>
    </swiper-slide>
  </swiper>
  <swiper
    :slides-per-view="3"
    :grid="{
      rows: 2
    }"
    :space-between="30"
    :pagination="{
      clickable: true
    }"
    :modules="[Grid, Pagination]"
    class="mySwiper"
  >
    <swiper-slide>Slide 1</swiper-slide>
    <swiper-slide>Slide 2</swiper-slide><swiper-slide>Slide 3</swiper-slide>
    <swiper-slide>Slide 4</swiper-slide><swiper-slide>Slide 5</swiper-slide>
    <swiper-slide>Slide 6</swiper-slide><swiper-slide>Slide 7</swiper-slide>
    <swiper-slide>Slide 8</swiper-slide><swiper-slide>Slide 9</swiper-slide>
  </swiper>
</template>
<script lang="ts" setup>
// Import Swiper Vue.js components
import { Grid, Pagination } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

// Import Swiper styles
import "swiper/css"

import "swiper/css/grid"
import "swiper/css/pagination"

defineProps<{
  novels: {
    img: string
    novel: string
    chap: string
    author: string
    status: string
    read: string
    genre: string

    route: {
      name: string
      params: {
        novel: number
      }
    }
    describe: string
  }[]
}>()

// import required modules
</script>-->
