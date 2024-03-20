<template>
  <q-card class="py-5">
    <swiper
      :style="{
        '--swiper-navigation-color': '#000',
        '--swiper-pagination-color': '#000'
      }"
      :slides-per-view="slidesPerView"
      :grid="{
        rows: 1
      }"
      :space-around="20"
      :loop="false"
      :navigation="true"
      :pagination="{
        clickable: true
      }"
      :modules="[Grid, Navigation]"
      class="mySwiper"
    >
      <swiper-slide
        v-for="novel in CountNovel"
        :key="novel.novel"
        class="to-transparent text-black! h-210px! px-5 swiperUpdate"
      >
        <router-link :to="novel.route">
          <div
            class="d-flex justify-start align-top h-200px w-105px img-hover-zoom"
          >
            <q-img
              :src="novel.img"
              class="w-100% h-140px rounded-5px"
              :ratio="1"
            />
            <q-item-label
              lines="2"
              class="text-16px text-bold hover:underline m-0.5"
              >{{ novel.novel }}</q-item-label
            >
            <div class="text-caption opacity-60">{{ novel.genre }}</div>
          </div>
          <!-- <q-card class="absolute-right w-70% h-100%">
            <q-card-section class="text-start text-16px text-black">
              <q-item-label class="text-h6 mb-2">{{
                novel.novel
              }}</q-item-label>
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
          </q-card> -->
        </router-link>
      </swiper-slide>
      <!-- <swiper-slide v-for="novel in NovelUpdates" :key="novel.novel">
      <router-link :to="novel.route">
        <q-img :src="novel.img" class="w-30%" :ratio="1" />
         <q-card class="absolute-right w-70% h-100%">
            <q-card-section class="text-start text-16px text-black">
              <q-item-label class="text-h6 mb-2">{{
                novel.novel
              }}</q-item-label>
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
      </router-link>
    </swiper-slide> -->
    </swiper>
  </q-card>
</template>
<script lang="ts" setup>
// Import Swiper Vue.js components
import { Grid, Navigation, Pagination } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

// Import Swiper styles
import "swiper/css"

import "swiper/css/grid"
import "swiper/css/navigation"
import "swiper/css/pagination"

const props = defineProps<{
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
  slidesPerView: number
}>()
const CountNovel = computed(() => {
  return props.novels.slice(0, 10)
})
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
<style>
body {
  font-family:
    Helvetica Neue,
    Helvetica,
    Arial,
    sans-serif;
  font-size: 14px;
  color: #000;
  margin: 0;
  padding: 0;
}
.swiper {
  width: 100%;
  height: 100%;
  margin-left: auto;
  margin-right: auto;
}

.swiperUpdates {
  text-align: center;
  font-size: 18px;
  width: 105px;
  /* height: calc((100% - 30px) / 2) !important; */

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}
.img-hover-zoom {
  overflow: hidden; /* Đảm bảo rằng không có phần nào của hình ảnh bị lộ ra ngoài khung chứa */
}

.img-hover-zoom img {
  transition: transform 0.5s ease; /* Đặt thời gian chuyển đổi và hiệu ứng */
}

.img-hover-zoom:hover img {
  transform: scale(1.2); /* Phóng to hình ảnh khi hover */
}
</style>
