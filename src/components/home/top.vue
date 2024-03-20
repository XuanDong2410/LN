<template>
  <div class="q-pa-md">
    <swiper
      :grab-cursor="true"
      :effect="'creative'"
      :loop="true"
      :autoplay="{
        delay: 4000,
        disableOnInteraction: false
      }"
      :navigation="{
        prevEl: '.pagination_prev',
        nextEl: '.pagination_next'
      }"
      :pagination="{
        clickable: true
      }"
      :creative-effect="{
        prev: {
          shadow: true,
          translate: ['-120%', 0, -500]
        },
        next: {
          shadow: true,
          translate: ['120%', 0, -500]
        }
      }"
      :modules="[Autoplay, EffectCreative, Navigation, Pagination]"
      class="mySwiper2"
    >
      <swiper-slide v-for="item in newUpdates" :key="item.index">
        <!-- <q-card class="h-100% w-50% text-black">

          <q-img :src="item.img" class="transparent" :ratio="1.5" />
        </q-card>  -->
        <q-card
          flat
          unelevated
          class="absolute-bottom-left ml-10 text-start w-50% h-80% transparent text-black opacity-400"
        >
          <q-card-section>
            <div class="text-h6 text-bold">
              {{ item.name }}
            </div>
            <div class="text-subtitle1">
              <q-chip class="bg-pink-400 text-white" square>Hot</q-chip>
              | {{ item.genre }} | {{ item.time }}
            </div>
            <div class="text-subtitle1">
              {{ item.author }}
            </div>
          </q-card-section>
          <q-card-actions align="left">
            <q-chip clickable color="pink" class="ml-1 text-start text-white">
              <q-icon class="size-2em"><i-ic-round-arrow-right /></q-icon>
              Read More
            </q-chip>
          </q-card-actions>
        </q-card>
      </swiper-slide>

      <button class="pagination pagination_prev fixed top-50% left-0 z-999">
        <i-gg-arrow-left-o class="size-2em" />
      </button>

      <button class="pagination pagination_next fixed top-50% right-0 z-999">
        <i-gg-arrow-right-o class="size-2em" />
      </button>
    </swiper>
  </div>
</template>
<script lang="ts" setup>
import {
  Autoplay,
  EffectCreative,
  Navigation,
  Pagination
} from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"
import "swiper/css"
import "swiper/css/pagination"
import "swiper/css/navigation"
const newUpdates = [
  {
    index: 1,
    name: "Già Thiên",
    chap: "Chương 391: Thôn thiên phệ địa",
    author: "Tây Hồ Long Đằng",
    user: "Ép Tiên Sinh",
    genre: "Đồng Nhân",
    time: "6 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 2,
    name: "Đánh Dấu Trăm Vạn Năm, Chế Tạo Vạn Cổ...",
    chap: "Chương 341: San bằng Thần Đình",
    author: "Thiên Thượng Tuyết Sương",
    user: "Ép Tiên Sinh",
    genre: "Huyền Huyễn",
    time: "12 phút trước",
    img: "https://cdn.quasar.dev/img/quasar.jpg"
  },
  {
    index: 3,
    name: "Quan Trường: Lên Như Diều Gặp Gió Chín...",
    chap: "Chương 655: Bên trên có chính sách dưới có đối sách?...",
    author: "Hỏa Liễu Mãi Phi Cơ",
    user: "Ép Tiên Sinh",
    genre: "Đô Thị",
    time: "16 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 4,
    name: "Vạn Cốt Chi Chủ",
    chap: "Chương 421: Huyền luyện cốt khí ( 2 )",
    author: "Lý Gia Huyền Nguyên",
    user: "Tiểu Miên Hoa",
    genre: "Huyền Huyễn",
    time: "17 phút trước",
    img: "https://cdn.quasar.dev/img/quasar.jpg"
  },
  {
    index: 5,
    name: "Già Thiên",
    chap: "Chương 391: Thôn thiên phệ địa",
    author: "Tây Hồ Long Đằng",
    user: "Ép Tiên Sinh",
    genre: "Đồng Nhân",
    time: "6 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 6,
    name: "Đánh Dấu Trăm Vạn Năm, Chế Tạo Vạn Cổ...",
    chap: "Chương 341: San bằng Thần Đình",
    author: "Thiên Thượng Tuyết Sương",
    user: "Ép Tiên Sinh",
    genre: "Huyền Huyễn",
    time: "12 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 7,
    name: "Quan Trường: Lên Như Diều Gặp Gió Chín...",
    chap: "Chương 655: Bên trên có chính sách dưới có đối sách?...",
    author: "Hỏa Liễu Mãi Phi Cơ",
    user: "Ép Tiên Sinh",
    genre: "Đô Thị",
    time: "16 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 8,
    name: "Vạn Cốt Chi Chủ",
    chap: "Chương 421: Huyền luyện cốt khí ( 2 )",
    author: "Lý Gia Huyền Nguyên",
    user: "Tiểu Miên Hoa",
    genre: "Huyền Huyễn",
    time: "17 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 9,
    name: "Đánh Dấu Trăm Vạn Năm, Chế Tạo Vạn Cổ...",
    chap: "Chương 341: San bằng Thần Đình",
    author: "Thiên Thượng Tuyết Sương",
    user: "Ép Tiên Sinh",
    genre: "Huyền Huyễn",
    time: "12 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  },
  {
    index: 10,
    name: "Vạn Cốt Chi Chủ",
    chap: "Chương 421: Huyền luyện cốt khí ( 2 )",
    author: "Lý Gia Huyền Nguyên",
    user: "Tiểu Miên Hoa",
    genre: "Huyền Huyễn",
    time: "17 phút trước",
    img: "https://static.cdnno.com/storage/topbox/272420578c5c7bc914b1ae4f03fab36a.webp"
  }
]
</script>
<style>
.mySwiper2 {
  width: 100% !important;
  height: 100%;
  margin-left: auto;
  margin-right: auto;
}

.swiper-slide {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
  font-weight: bold;
  border: none;
  color: #940808;
  width: 100%;
  height: 100%;
}
</style>
