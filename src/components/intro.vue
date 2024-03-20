<template>
  <div class="row">
    <q-card class="col-md-8">
      <q-card-section class="q-pt-none text-body2">
        .....
        <br />
        800 năm trước, Minh Đế chi tử Trương Nhược Trần, bị vị hôn thê của hắn
        Trì Dao công chúa giết chết, thiên kiêu một đời, liền như vậy ngã xuống.
        Tám trăm năm sau, Trương Nhược Trần một lần nữa sống lại, lại phát hiện
        vị hôn thê đã từng giết chết hắn, đã thống nhất Côn Lôn Giới, mở ra Đệ
        Nhất Trung Ương đế quốc, được xưng "Trì Dao Nữ Hoàng" .
        <br />
        Trì Dao Nữ Hoàng —— thống ngự thiên hạ, uy lâm bát phương; thanh xuân
        mãi mãi, bất tử bất diệt. Trương Nhược Trần đứng ở Chư Hoàng Từ Đường ở
        ngoài, nhìn Trì Dao Nữ Hoàng tượng thần, trong lòng bốc cháy lên hừng
        hực cừu hận liệt diễm, "Đợi ta trùng tu mười ba năm, dám gọi Nữ Hoàng
        dưới Hoàng Tuyền" .
        <br />
        TG: Thần Ma Thiên Tôn, Linh Chu. TG đổi tên.
      </q-card-section>
      <q-separator />
      <q-card-section class="q-pt-none text-caption mt-3">
        <q-btn flat class="text-bold text-capitalize" label="Tên khác" /> <br />
        <q-btn
          v-for="{ name } in names"
          flat
          class="text-caption text-capitalize"
          :label="name"
        />
      </q-card-section>
      <q-separator />
      <q-card-section class="q-pt-none text-body2 mt-3 row">
        <q-btn flat class="text-bold text-capitalize" label="Cảm xúc" />
        <!-- <q-toolbar class="d-flex justify-between m-0"> -->
        <div class="col-12 d-flex justify-center text-center wrap">
          <q-chip
            v-for="{ icon, number } in emojis"
            text
            unelevated
            rounded
            class="text-black bg-white"
            align="center"
            no-caps
          >
            <Component :is="icon" class="size-2.5em" clickable />
            <div class="d-flex mt-2">{{ number }}</div>
          </q-chip>
        </div>
        <!-- </q-toolbar> -->
      </q-card-section>

      <q-separator />
      <q-card-section class="q-pt-none text-caption mt-3">
        <q-btn flat class="text-bold text-capitalize" label="Chương mới" />
        <q-btn flat class="text-caption text-capitalize" :label="chaps.name" />
        <q-btn class="text-caption text-capitalize" unelevated>{{
          chaps.time
        }}</q-btn>
      </q-card-section>
    </q-card>
    <q-card class="col-md-4 d-flex justify-center m-0 bg-#eee bg-opacity-48">
      <q-card-section class="text-center">
        <router-link :to="author.route">
          <div class="relative inline-block">
            <q-avatar size="84px">
              <q-img :src="author.img" />
            </q-avatar>
            <div
              class="py-1px leading-normal px-3 text-13px min-w-0 rounded-xl bg-red-600 whitespace-nowrap absolute bottom--0 py-0 text-white left-1/2 translate-x--1/2"
            >
              {{ author.level.name }}
            </div>
          </div>
          <h6 class="text-18px font-600 mt-2">{{ author.name }}</h6>
        </router-link>
      </q-card-section>
      <q-card-section>
        <q-toolbar class="row text-body2 text-center">
          <div class="col-4 d-flex justify-center">
            <i-fa6-solid:book class="size-2.25em mx-auto" />
            <h6>Số truyện</h6>
            {{ author.numbernovels }}
          </div>
          <div class="col-4">
            <i-subway-book class="size-2.5em mx-auto" />
            <h6>Số chương</h6>
            {{ author.numberchaps }}
          </div>
          <div class="col-4">
            <i-solar-medal-ribbon-star-bold class="size-3em mx-auto" />
            <h6>Cấp</h6>
            <hr />
            {{ author.level.value }}
          </div>
        </q-toolbar>
      </q-card-section>
      <q-card-section>
        <swiper
          :loop="true"
          :pagination="{
            type: 'custom',
            clickable: true
          }"
          :navigation="true"
          :modules="[Navigation, Pagination]"
          class="max-w-120"
        >
          <swiper-slide v-for="novel in novels" class="text-center w-100%">
            <q-card
              class="no-bow-shadow text-16px bg-#eee w-100% d-flex justify-center text-black p-2"
            >
              <q-img :src="novel.img" class="w-30% mx-auto row m-2" />
              <q-item-label class="">{{ novel.name }}</q-item-label>
              <q-item-label class="text-caption m-4" lines="3">
                {{ novel.description }}
              </q-item-label>
              <q-btn
                square
                outline
                unelevated
                class="bg-white text-yellow-400"
                >{{ novel.genre }}</q-btn
              >
            </q-card>
          </swiper-slide>
        </swiper>
      </q-card-section>
    </q-card>
  </div>
</template>
<script lang="ts" setup>
// Import Swiper styles
import "swiper/css"

import "swiper/css/pagination"
import "swiper/css/navigation"

// Import Swiper Vue.js components
import { Navigation, Pagination } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

// import required modules

import angry from "~icons/fluent-emoji-flat/angry-face"
import fire from "~icons/fluent-emoji-flat/fire"
import heart from "~icons/fluent-emoji-flat/red-heart"
import sad from "~icons/fluent-emoji-flat/sad-but-relieved-face"
import smile from "~icons/fluent-emoji-flat/smiling-face-with-smiling-eyes"
import like from "~icons/fluent-emoji-flat/thumbs-up"

const names = [
  {
    name: "Vạn Cổ Thần Đế"
  },
  {
    name: "Trì Dao Nữ Hoàng"
  },
  {
    name: "Chuyển sinh thành nhện"
  }
]
const chaps = {
  name: "Chương 4173: Người trong quan tài",
  time: "8 giờ trước"
}

const author = {
  img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
  name: "DarkHero",
  numbernovels: 186,
  numberchaps: "177,7k",
  level: {
    value: 4,
    name: "Kim Cương"
  },
  route: {
    name: "profile/profile",
    params: {
      user: "DarkHero"
    }
  }
}
const emojis = [
  {
    name: "hearts",
    icon: heart,
    number: 85443
  },
  {
    name: "like",
    icon: like,
    number: 79235
  },
  {
    name: "fire",
    icon: fire,
    number: 15861
  },
  {
    name: "smile",
    icon: smile,
    number: 28147
  },
  {
    name: "sad",
    icon: sad,
    number: 7039
  },
  {
    name: "angry",
    icon: angry,
    number: 2244
  }
]
const novels = [
  {
    img: "https://static.cdnno.com/poster/dai-dao-vo-cuc/150.jpg?1632478682",
    name: "Nhân Đạo Đại Thánh",
    genre: "Huyền Huyễn",
    description:
      "Kẻ yếu khàn cả giọng, cũng không có người quan tâm, cường giả nhẹ giọng thì thầm, lại có thể xâm nhập"
  },
  {
    img: "https://static.cdnno.com/poster/quoc-vuong-1/150.jpg?1663492433",
    name: "Quốc Vương",
    genre: "Kỳ Ảo",
    description:
      "Vạn tộc cùng tồn tại, kiếm cùng ma pháp hoà lẫn, Nhân tộc, Hải tộc, Tinh Linh, Ải Nhân, Thú Nhân... Giành trước nở rộ văn minh chi quang, viết lên sử thi bi ca!"
  },
  {
    img: "https://static.cdnno.com/poster/tham-hai-du-tan/150.jpg?1685260612",
    name: "Thâm Hải Dư Tẫn",
    genre: "Khoa Huyễn",
    description:
      "Tại ngày đó, nồng vụ phong tỏa hết thảy.Tại ngày đó, hắn trở thành một chiếc u linh thuyền thuyền trưởng."
  }
]
</script>
