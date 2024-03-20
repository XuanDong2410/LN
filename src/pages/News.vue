<template>
  <q-page>
    <q-toolbar>
      <q-btn
        v-for="{ name, icon, menus } in searchs"
        text
        unelevated
        rounded
        class="text-black"
        no-caps
      >
        {{ name }}
        <Component :is="icon" class="size-1em ml-1" />
        <q-menu transition-show="jump-down" transition-hide="jump-up">
          <q-list style="min-width: 100px">
            <q-item v-for="{ select } in menus" clickable>
              <q-item-section>{{ select }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
      <q-space />
      <q-btn class="p-2 capitalize" @click="GenreDialog = !GenreDialog"
        ><i-akar-icons-sort
      /></q-btn>
    </q-toolbar>
    <div class="q-pa-md mx-10 max-w-1300px d-flex justify-center">
      <!-- <div class="row col-12 q-pr-none">
        <q-infinite-scroll @load="onLoad" :offset="250" class="w-100% p-0 w-0"> -->
      <!-- <q-intersection
          v-for="(novel, index) in Novels"
          :key="index"
          transition="scale"
          class="example-item m-1 w-30"
          > -->
      <div class="d-flex justify-start row w-100% mx-auto">
        <q-card
          bordered
          class="w-45 h-60 mx-4 my-4 img-hover-zoom"
          v-ripple
          clickable
          v-for="(novel, index) in data"
          :key="index"
        >
          <router-link :to="novel.route">
            <q-img :ratio="178 / 191" :src="novel.img" :alt="novel.name" />

            <q-card-section class="p-1">
              <q-item-label lines="2" class="text-subtitle text-center mt-1">
                {{ novel.name }}
                <q-tooltip
                  anchor="center middle"
                  self="center middle"
                  class="bg-gray-100 w-275px p-3"
                >
                  <div class="text-black">
                    <q-item-label class="text-yellow-600 text-18px" max="30">
                      {{ novel.name }}
                    </q-item-label>
                    <q-chip
                      square
                      class="text-light-300 bg-blue-400 text-12px m-0.25 p-1"
                      v-for="genre in novel.genres"
                      >{{ genre }}</q-chip
                    >
                    <h6>Lượt xem: {{ novel.view }}</h6>
                    <h6>Lượt theo dõi: {{ novel.sub }}</h6>

                    <q-item-label lines="3">
                      {{ novel.describe }}
                    </q-item-label>
                  </div>
                </q-tooltip>
              </q-item-label>
              <!-- <q-item-label class="text-subtitle2">{{ chap }}</q-item-label> -->
            </q-card-section>
          </router-link>
        </q-card>
      </div>
      <div class="py-5">
        <q-pagination
          v-model="current"
          :max="max"
          direction-links
          color="orange"
          active-design="unelevated"
          active-color="brown"
          active-text-color="orange"
          class="absolute-bottom-right m-3"
          align="center"
        />
      </div>
    </div>
    <q-dialog v-model="GenreDialog" :position="'top'">
      <div class="row mt-2">
        <q-card class="w-800px">
          <div class="flex items-center px-4 py-2 justify-between">
            <div class="text-h6">Bo loc</div>
            <q-btn
              icon="close"
              unelevated
              round
              class="p-2 size-3em"
              @click="GenreDialog = false"
            />
          </div>
          <q-list class="opacity-80">
            <q-expansion-item
              default-opened
              label="Genres"
              class="w-100% d-flex justify-around"
              popup
            >
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in Genres"
                  :key="item.id"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>

            <q-separator />
            <q-expansion-item label="Status" class="w-100%" popup>
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in status"
                  :key="item.name"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>

            <q-separator />
            <q-expansion-item label="Tính cách nhân vật" class="w-100%" popup>
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in Character"
                  :key="item.id"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>

            <q-separator />
            <q-expansion-item label="Bối cảnh thế giới" class="w-100%" popup>
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in WorldBuild"
                  :key="item.id"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>
            <q-separator />
            <q-expansion-item label="Lưu phái" class="w-100%" popup>
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in Character"
                  :key="item.id"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>
            <q-separator />
            <q-expansion-item label="Thị giác" class="w-100%" popup>
              <div class="m-0.5 py-1">
                <q-chip
                  class="text-opacity-5 hover:text-orange-400"
                  v-for="item in Character"
                  :key="item.id"
                  clickable
                  outline
                >
                  {{ item.name }}
                </q-chip>
              </div>
            </q-expansion-item>
          </q-list>
          <div class="py-2 w-100%" align="right">
            <!-- <q-btn class="m-2">Sort</q-btn> -->
          </div>
        </q-card>
      </div>
    </q-dialog>
    <!-- </div> -->
  </q-page>
</template>
<script lang="ts" setup>
import WorldBuild from "../data/genre/Worldbuild.json"
import Character from "../data/genre/characters.json"
import Genres from "../data/genre/genres.json"
import Novels from "../data/novel.json"

import IconDown from "~icons/ant-design/caret-down-filled"

const current = ref(1)
const max = Novels.length / 15 + 1
const data = computed(() => {
  const itemsPerPage = 15
  const startIndex = (current.value - 1) * itemsPerPage
  const endIndex = startIndex + itemsPerPage
  return Novels.slice(startIndex, endIndex)
})
const GenreDialog = ref(false)
const searchs = [
  {
    name: "Mới cập nhật",
    icon: IconDown,
    menus: [
      {
        select: "Mới cập nhật"
      },
      {
        select: "Mới đăng"
      }
    ]
  },
  {
    name: "Lượt đọc",
    icon: IconDown,
    menus: [
      {
        select: "Lượt đọc [ngày]"
      },
      {
        select: "Lượt đọc [tuần]"
      },
      {
        select: "Lượt đọc [tháng]"
      },
      {
        select: "Lượt đọc [toàn]"
      }
    ]
  },
  {
    name: "Điểm đánh giá",
    icon: IconDown,
    menus: [{ select: "Lượt đánh giá" }, { select: "Điểm đánh giá" }]
  },
  {
    name: "Yêu thích",
    icon: ""
  },
  {
    name: "Bình luận",
    icon: ""
  },
  {
    name: "Số chương",
    icon: ""
  }
]
const status = [
  {
    name: "Đang tiến hành"
  },
  {
    name: "Tạm ngưng"
  },
  {
    name: "Hoàn thành"
  }
]
// function onLoad(index: number, novels: any) {
//   setTimeout(() => {
//     Novels.push(Novels[index], Novels[index])
//     Novels.push(Novels[index])
//     novels()
//   }, 2000)
// }
// const max = Novels.length / 10 + 1
// const data = computed(() => {
//   const itemsPerPage = 10
//   const startIndex = (current.value - 1) * itemsPerPage
//   const endIndex = startIndex + itemsPerPage
//   return Novels.slice(startIndex, endIndex)
// })
// const current = ref(1)
</script>
<style>
.img-novel {
  box-shadow: 4px 4px 6px rgba(0, 0, 0, 0.3);
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
