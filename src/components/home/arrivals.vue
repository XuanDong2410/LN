<template>
  <q-card class="row max-w-1200px mx-auto text-black!">
    <div class="col-7 py-3">
      <swiper
        @swiper="setThumbsSwiper"
        :space-between="1"
        :slides-per-view="10"
        :free-mode="true"
        :watch-slides-progress="true"
        :modules="[FreeMode, Thumbs]"
        class="swiperShow1 imgShow max-h-100px!"
      >
        <swiper-slide v-for="novel in CountNovelSwiper" class="img-hover-zoom">
         
            <q-img
              :src="novel.img"
              class="w-54px h-72px b-blue-600 b-solid rounded-5px mx-2"
            />
        </swiper-slide>
      </swiper>
      <swiper
        :loop="true"
        :space-between="10"
        :thumbs="{ swiper: getThumbsSwiper() }"
        :modules="[FreeMode, Thumbs]"
        class="swiperShow"
      >
        <swiper-slide v-for="novel in CountNovelSwiper" class="">
          <q-item flat class="col-6 row cursor-pointer">
            <q-item-section avatar class="m-0 w-120px! img-hover-zoom">
              <q-img
                :src="novel.img"
                class="w-120px! h-160px img-novel rounded-5px"
                :ratio="1"
              />
            </q-item-section>
            <q-card-section class="d-flex align-top justify-start! col-9">
              <q-item-label
                lines="2"
                class="text-bold text-20px hover:text-orange-400"
                >{{ novel.name }}</q-item-label
              >
              <q-item-label class="text-14px opacity-90 hover:text-orange-400">
                {{ novel.genre }}
              </q-item-label>
              <q-item-label
                lines="3"
                class="text-11px text-justify text-body2 opacity-70"
              >
                {{ novel.describe }}
              </q-item-label>
              <div class="py-1">
                <q-btn class="rounded-10px bg-blue-600 text-light-300">
                  READ NOW
                  <q-tooltip>Read Now</q-tooltip>
                </q-btn>
                <q-btn round class="m-1">
                  <i-ic:baseline-plus class="size-2em" />
                  <q-tooltip>Add to library</q-tooltip>
                </q-btn>
              </div>
            </q-card-section>
          </q-item>
        </swiper-slide>
      </swiper>
    </div>
    <div class="col-5 row">
      <q-item flat v-for="novel in CountNovel" class="col-6 row cursor-pointer">
        <q-item-section avatar class="m-0 img-hover-zoom">
          <q-img :src="novel.img" class="w-60px h-80px img-novel" :ratio="1" />
        </q-item-section>
        <q-card-section class="d-flex align-top! justify-start!">
          <q-item-label
            lines="2"
            class="text-bold text-13px hover:text-orange-400"
            >{{ novel.name }}</q-item-label
          >
          <q-item-label caption class="hover:text-orange-400">{{
            novel.genre
          }}</q-item-label>
        </q-card-section>
      </q-item>
    </div>
  </q-card>
</template>
<script lang="ts" setup>
import { FreeMode, Thumbs } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

import "swiper/css"

import "swiper/css/free-mode"

import "swiper/css/thumbs"
const props = defineProps<{
  novels: {
    img: string
    name: string
    genre: string
    describe: string
  }[]
}>()
const thumbsSwiper = ref(null)

const setThumbsSwiper = (swiper: any) => {
  if (swiper) {
    thumbsSwiper.value = swiper
  }
}
function getThumbsSwiper() {
  return thumbsSwiper.value
}
const CountNovel = computed(() => {
  return props.novels.slice(0, 6)
})
const CountNovelSwiper = computed(() => {
  return props.novels.slice(0, 12)
})
</script>
<style>
.img-novel {
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.3);
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

.swiperShow1 {
  background-size: cover;
  background-position: center;
}

.swiperThumb .swiper-slide-thumb-active {
  border: 2px solid blue;
  opacity: 0.2;
}
.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
