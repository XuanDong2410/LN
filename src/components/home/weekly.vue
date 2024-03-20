<template>
  <q-card class="row max-w-1200px max-h-500px mx-auto">
    <div class="col-4">
      <swiper
        :style="{
          '--swiper-navigation-color': '#fff',
          '--swiper-pagination-color': '#fff'
        }"
        :autoplay="{
          delay: 2500,
          disableOnInteraction: false
        }"
        :loop="true"
        :speed="600"
        :parallax="true"
        :pagination="{
          clickable: true
        }"
        :navigation="true"
        :modules="[Autoplay, Navigation, Pagination, Parallax]"
        class="SwiperWeekly"
      >
        <swiper-slide
          v-for="novel in CountNovelSwiper"
          class="text-black! max-h-410px! bg-gray-300 py-5 cursor-pointer swiperWeekly"
        >
          <div
            class="parallax-bg img-container opacity-60 to-transparent"
            data-swiper-parallax="-23%"
          >
            <q-img :src="novel.img" class="h-100% w-100%" :ratio="1" />
          </div>
          <div class="w-100% d-flex justify-center my-100!">
            <q-img
              :src="novel.img"
              class="w-120px h-160px rounded-4px m-3 box-shadow:'1px 1px 1px rgba(0,0,0,0.1)'"
            /><q-item class="to-transparent opacity-90">
              <q-item-section class="d-flex justify-start!">
                <q-item-label
                  lines="2"
                  class="text-18px hover:text-orange-600 hover:text-bold"
                  data-swiper-parallax="-300"
                >
                  {{ novel.name }}
                </q-item-label>
                <q-item-label class="text-subtitle" data-swiper-parallax="-200">
                  <q-chip square outline class="hover:text-amber">
                    {{ novel.genre }}
                  </q-chip>
                </q-item-label>
                <q-item-label
                  text-caption
                  lines="4"
                  class="text-caption"
                  data-swiper-parallax="-100"
                >
                  <p>{{ novel.describe }}</p>
                </q-item-label>
              </q-item-section>
            </q-item>
          </div>
        </swiper-slide>
      </swiper>
    </div>

    <div class="col-8 d-flex justify-around nowrap row">
      <q-card
        v-for="novel in CountNovel"
        flat
        class="w-105px h-210px cursor-pointer img-hover-zoom mx-5"
      >
        <q-img :src="novel.img" />
        <q-item-label
          lines="2"
          class="text-bold opacity-90 hover:opacity-200 my-0.5"
        >
          {{ novel.name }}
        </q-item-label>
        <q-item-label
          lines="2"
          class="text-caption opacity-90 hover:opacity-200 my-0.5"
        >
          {{ novel.genre }}
        </q-item-label>
      </q-card>
    </div>
  </q-card>
</template>
<script lang="ts" setup>
import { Autoplay, Navigation, Pagination, Parallax } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

// Import Swiper styles
import "swiper/css"

import "swiper/css/pagination"
import "swiper/css/navigation"

// import required modules
const props = defineProps<{
  novels: {
    img: string
    name: string
    genre: string
    describe: string
  }[]
}>()
const CountNovel = computed(() => {
  return props.novels.slice(0, 10)
})
const CountNovelSwiper = computed(() => {
  return props.novels.slice(0, 5)
})
</script>
<style>
.SwiperWeekly {
  width: 100%;
  height: 100%;
}

.swiperWeekly {
  font-size: 18px;
  color: #fff;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  padding: 40px 60px;
  text-align: center;
  font-size: 18px;
  width: 105px;
  /* height: calc((100% - 30px) / 2) !important; */

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
}

.parallax-bg {
  position: absolute;
  left: 0;
  top: 0;
  width: 130%;
  height: 410px;
  -webkit-background-size: cover;
  background-size: cover;
  background-position: center;
}

.swiper-slide .title {
  font-size: 41px;
  font-weight: 300;
}

.swiper-slide .subtitle {
  font-size: 21px;
}

.swiper-slide .text {
  font-size: 14px;
  max-width: 400px;
  line-height: 1.3;
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
.img-container img {
  width: 100%; /* Đặt chiều rộng của hình ảnh bằng với thẻ div bên ngoài */
  height: auto; /* Đặt chiều cao tự động để giữ nguyên tỉ lệ */
  object-fit: cover; /* Đảm bảo hình ảnh vừa vặn và che kín thẻ div */
  filter: blur(5px); /* Làm mờ hình ảnh */
  transition: filter 0.3s ease; /* Tạo hiệu ứng chuyển đổi mượt mà */
}

/* .img-container:hover img {
  filter: blur(0px); /* Khi hover, hình ảnh sẽ trở nên rõ nét
} */
</style>
