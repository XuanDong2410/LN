<route lang="yaml">
name: "novel"
</route>

<template>
  <q-page class="max-w-1200px mx-auto">
    <q-card class="my-card m-5" flat bordered>
      <div class="wrap row">
        <div class="col-2 img-hover-zoom">
          <q-img :src="novels.img" class="w-100% h-60 col-3 m-2 img-novel" />
        </div>

        <q-card-section class="col-8 ml-3">
          <div class="row wrap items-center">
            <div class="col text-h4 ellipsis">
              {{ novel }} {{ novels.name }}
            </div>
            <q-btn unelevated rounded @click="report = true"
              ><q-icon name="flag"
            /></q-btn>
          </div>
          <div class="text-subtitle1">
            <q-item-label class="text-h7">
              Thể loại:
              <q-chip
                class="text-green text-h7 bg-light-400"
                v-for="{ name } in genres"
                clickable
              >
                {{ name }}
              </q-chip>
            </q-item-label>
            <q-item-label class="text-h7">
              Tác giả:
              <q-chip class="text-red text-h7 bg-light-400" clickable>
                {{ novels.author }}
              </q-chip>
            </q-item-label>
            <q-item-label class="text-h7">
              Tình trạng:
              <q-chip class="text-h7 bg-light-100">
                {{ novels.status }}
              </q-chip>
            </q-item-label>
          </div>
          <div class="text-h6 ml-3 text-opacity-40 row">
            <h6 class="col-2">
              <p class="row-12">{{ novels.chapters }}</p>
              <p class="row-12 text-caption text-opacity-400">Chương</p>
            </h6>
            <h6 class="col-2">
              <p class="row-12">{{ novels.chapInWeek }}</p>
              <p class="row-12 text-caption text-opacity-400">Chương/tuần</p>
            </h6>
            <h6 class="col-2">
              <p class="row-12">{{ novels.read }}</p>
              <p class="row-12 text-caption text-opacity-400">Lượt đọc</p>
            </h6>
            <h6 class="col-2">
              <p class="row-12">{{ novels.favorites }}</p>
              <p class="row-12 text-caption text-opacity-400">Cất giữ</p>
            </h6>
          </div>
          <div class="q-pa-md">
            <q-rating
              name="quality"
              v-model="novels.vote.value"
              max="5"
              size="2em"
              color="yellow"
              icon="star_border"
              icon-selected="star"
              no-dimming
            />
            {{ novels.vote.value }}/ 5 ({{ novels.vote.number }} đánh giá)
          </div>
          <q-btn class="bg-red text-white" rounded>
            <Component :is="Read" class="size-2em m-2" /> Đọc tiếp</q-btn
          >

          <q-btn class="ml-3" v-model:selected="Isbookmark" rounded
            ><Component :is="NoneBookmark" class="size-2em m-2" />Đánh
            dấu</q-btn
          >
        </q-card-section>
      </div>

      <q-separator />
    </q-card>
    <!-- <intro /> -->
    <div class="row">
      <q-card class="col-md-8">
        <q-card-section class="q-pt-none text-body2 text-justify">
          {{ novels.describe }}
        </q-card-section>
        <q-separator />
        <q-card-section class="q-pt-none text-caption mt-3">
          <q-btn flat class="text-bold text-capitalize" label="Tên khác" />
          <br />
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
          <q-btn
            flat
            class="text-caption text-capitalize"
            :label="chaps.name"
          />
          <q-btn class="text-caption text-capitalize" unelevated>{{
            chaps.time
          }}</q-btn>
        </q-card-section>
      </q-card>
      <q-card class="col-md-4 d-flex justify-center m-0 bg-#eee bg-opacity-48">
        <q-card-section class="text-center">
          <div class="relative inline-block">
            <route-link :to="author.route">
              <q-avatar size="84px">
                <q-img :src="author.img" />
              </q-avatar>
            </route-link>
            <div
              class="py-1px leading-normal px-3 text-13px min-w-0 rounded-xl bg-red-600 whitespace-nowrap absolute bottom--0 py-0 text-white left-1/2 translate-x--1/2"
            >
              {{ author.level.name }}
            </div>
          </div>
          <route-link :to="author.route">
            <h6>
              <q-btn
                class="text-16px font-600 mt-2"
                unelevated
                rounded
                :to="author.route"
                >{{ author.name }}</q-btn
              >
            </h6>
          </route-link>
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
            <swiper-slide
              v-for="Anovels in AuthorNovels"
              class="text-center w-100%"
            >
              <div
                class="w-100% d-flex justify-center cursor-pointer img-hover-zoom"
              >
                <q-img
                  :src="Anovels.img"
                  class="w-120px h-160px rounded-4px m-3 img-novel"
                /><q-item class="to-transparent opacity-90">
                  <q-item-section class="d-flex justify-start!">
                    <q-item-label
                      lines="2"
                      class="text-18px hover:text-orange-600 hover:text-bold"
                      data-swiper-parallax="-300"
                    >
                      {{ Anovels.name }}
                    </q-item-label>

                    <q-item-label
                      text-caption
                      lines="4"
                      class="text-caption"
                      data-swiper-parallax="-100"
                    >
                      <p>{{ Anovels.description }}</p>
                    </q-item-label>
                    <q-item-label
                      class="text-subtitle"
                      data-swiper-parallax="-200"
                    >
                      <q-chip square outline class="hover:text-amber">
                        {{ Anovels.genre }}
                      </q-chip>
                    </q-item-label>
                  </q-item-section>
                </q-item>
              </div>
            </swiper-slide>
          </swiper>
        </q-card-section>
      </q-card>
    </div>
    <chapters />
    <comment />
    <!-- <q-card item="infors" class="m-5">
      <q-tabs
        v-model="tab"
        align="left"
        class="text-5em h-50px d-flex justify-start"
        dense
        indicator-color="cyan"
        narrow-indicator
      >
        <q-tab
          class="text-4em"
          v-for="info in infors"
          :key="info.name"
          :name="info.name"
          :label="info.name"
        >
           <q-badge outline align="middle" >{{ info.number }}</q-badge>
        </q-tab>
      </q-tabs>
      <q-separator />
      <q-tab-panels v-model="tab" animated>
        <q-tab-panel v-for="info in infors" :name="info.name">
          <Component :is="info.value" />
        </q-tab-panel>
      </q-tab-panels>
    </q-card> -->
    <q-dialog v-model="report" position="top">
      <Report />
    </q-dialog>
  </q-page>
</template>
<script lang="ts" setup>
import "swiper/css"

import "swiper/css/pagination"
import "swiper/css/navigation"

// Import Swiper Vue.js components
// import Intro from "components/intro.vue"
import Comment from "components/novel/comment.vue"
import Report from "components/report.vue"
import chapters from "src/components/novel/chapters.vue"
import { Navigation, Pagination } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

// import required modules

// import { reactive } from "vue"
import Read from "~icons/ant-design/read-filled"
import angry from "~icons/fluent-emoji-flat/angry-face"
import fire from "~icons/fluent-emoji-flat/fire"
import heart from "~icons/fluent-emoji-flat/red-heart"
import sad from "~icons/fluent-emoji-flat/sad-but-relieved-face"
import smile from "~icons/fluent-emoji-flat/smiling-face-with-smiling-eyes"
import like from "~icons/fluent-emoji-flat/thumbs-up"
import NoneBookmark from "~icons/mdi/bookmark-outline"

// import Vote from "components/vote.vue"

// import bookmark from "~icons/ic/bookmark"
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
    name: "profile",
    params: {
      profile: "DarkHero"
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
const AuthorNovels = [
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
// import Chapter from "components/chapters.vue"

const report = ref(false)
// const position = ref("top")
const novels = {
  name: "Kumo Desu Ga Nani Ka",
  img: "https://3.bp.blogspot.com/-coc62nTZN9M/WO2v-JFMCuI/AAAAAAAAKBE/Kb8JLmHVElw/w215/series_259.jpg",

  chapters: 4386,
  chapInWeek: 18,
  numbers: 4386,
  read: "39.2M",
  favorites: 12972,
  author: "Baba Okina",
  status: "Đang tiến hành",
  describe:
    "....800 năm trước, Minh Đế chi tử Trương Nhược Trần, bị vị hôn thê của hắn.Trì Dao công chúa giết chết, thiên kiêu một đời, liền như vậy ngã.xuống. Tám trăm năm sau, Trương Nhược Trần một lần nữa sống lại, lại.phát hiện vị hôn thê đã từng giết chết hắn, đã thống nhất Côn Lôn.Giới, mở ra Đệ Nhất Trung Ương đế quốc, được xưng 'Trì Dao Nữ Hoàng' ...Trì Dao Nữ Hoàng —— thống ngự thiên hạ, uy lâm bát phương; thanh xuân.mãi mãi, bất tử bất diệt. Trương Nhược Trần đứng ở Chư Hoàng Từ Đường.ở ngoài, nhìn Trì Dao Nữ Hoàng tượng thần, trong lòng bốc cháy lên.hừng hực cừu hận liệt diễm, 'Đợi ta trùng tu mười ba năm, dám gọi Nữ.Hoàng dưới Hoàng Tuyền' ..." +
    "\t" +
    "TG: Thần Ma Thiên Tôn, Linh Chu. TG đổi tên",
  vote: {
    number: 18,
    value: 4.77
  }
}

defineProps<{ novel: string }>()
const Isbookmark = reactive({
  Is: false
})
const genres = [
  {
    name: "Action"
  },
  {
    name: "Comedy"
  },
  {
    name: "Drama"
  },
  {
    name: "Harem"
  }
]
// const infors = [
//   {
//     name: "Giới thiệu",
//     number: 0,
//     value: Intro
//   },
//   {
//     name: "Đánh giá",
//     number: 2000,
//     value: Vote
//   },
//   {
//     name: "D.s chương",
//     number: 4173,
//     value: Chapter
//   },
//   {
//     name: "Bình luận",
//     number: false,
//     value: Comment
//   }
// ]
// const note = [
//   {
//     name: "Chú thích thêm",
//     description: ""
//   }
// ]
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
</style>
