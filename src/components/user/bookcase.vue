<template>
  <q-tabs
    v-model="tab"
    active-color="orange"
    indicator-color="orange"
    align="left"
    class="ml-3"
  >
    <q-tab
      name="reading"
      label="Reading"
      inline-label
      class="text-capitalize"
    />
    <q-tab
      name="favorites"
      label="Favorites"
      inline-label
      class="text-capitalize"
    />
    <q-tab
      name="bookmark"
      label="Bookmark"
      inline-label
      class="text-capitalize"
    />
  </q-tabs>

  <q-tab-panels v-model="tab" animated>
    <q-tab-panel name="reading" class="q-pa-none">
      <q-list class="mb-10">
        <q-item v-for="(novel, index) in data" :key="index">
          <q-item-section avatar>
            <q-img :src="novel.img" size="1em" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ novel.name }}</q-item-label>
            <q-item-label class="text-caption opacity-70"
              >Đã đọc : {{ novel.read }} / {{ novel.number }}</q-item-label
            >
          </q-item-section>
          <q-item-section thumbnail>
            <q-icon size-0.5em> <i-fluent-alert-16-filled /> </q-icon>
          </q-item-section>
          <q-item-section thumbnail>
            <q-icon size-0.5em> <i-mdi-trash /> </q-icon>
          </q-item-section>
        </q-item>
      </q-list>
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
    </q-tab-panel>
    <q-tab-panel name="favorites" class="q-pa-none">
      <q-list class="mb-10">
        <q-item v-for="(novel, index) in data" :key="index">
          <q-item-section avatar>
            <q-img :src="novel.img" size="1em" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ novel.name }}</q-item-label>
          </q-item-section>
          <q-item-section thumbnail>
            <q-icon size-0.5em> <i-pepicons-pop-dots-y /> </q-icon>
          </q-item-section>
        </q-item>
      </q-list>
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
    </q-tab-panel>
    <q-tab-panel name="bookmark" class="q-pa-none">
      <q-list class="mb-10">
        <q-item v-for="(novel, index) in data" :key="index">
          <q-item-section avatar>
            <q-img :src="novel.img" size="1em" />
          </q-item-section>
          <q-item-section>
            <q-item-label>{{ novel.name }}</q-item-label>
            <q-item-label class="text-caption opacity-70"
              >Đánh dấu : {{ novel.bookmark }} /
              {{ novel.number }}</q-item-label
            >
          </q-item-section>
          <q-item-section thumbnail>
            <q-icon size-0.5em> <i-fluent-alert-16-filled /> </q-icon>
          </q-item-section>
          <q-item-section thumbnail>
            <q-icon size-0.5em> <i-mdi-trash /> </q-icon>
          </q-item-section>
        </q-item>
      </q-list>
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
    </q-tab-panel>
  </q-tab-panels>
</template>

<script lang="ts" setup>
import { ref } from "vue"
const tab = ref("reading")
const current = ref(1)
const listNovel = [
  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 213,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },
  {
    id: 2,
    name: "Tận Thế: Ta Có Thể Trông Thấy Thanh Máu, Giết Quái Rơi Bảo",
    read: 215,
    bookmark: null,
    number: 714,
    img: "https://static.cdnno.com/poster/tan-the-ta-co-the-trong-thay-thanh-mau-giet-quai-roi-bao/150.jpg?1706957067"
  },
  {
    id: 3,
    name: "Huyền lục",
    read: 201,
    bookmark: null,
    number: 2077,
    img: "https://static.cdnno.com/poster/huyen-luc/150.jpg?1652019253"
  },
  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 4431,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },
  {
    id: 4,
    name: "Xích tâm tuần thiên",
    read: 123,
    number: 2328,
    bookmark: null,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612"
  },

  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 4431,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },
  {
    id: 5,
    name: "Lãnh Chúa Cầu Sinh: Từ Tàn Tạ Tiểu Viện Bắt Đầu Công Lược",
    read: 1427,
    number: 1428,
    bookmark: null,
    img: "https://static.cdnno.com/poster/lanh-chua-cau-sinh-tu-tan-ta-tieu-vien-bat-dau-cong-luoc/150.jpg?1622827604"
  },
  {
    id: 2,
    name: "Tận Thế: Ta Có Thể Trông Thấy Thanh Máu, Giết Quái Rơi Bảo",
    read: 215,
    bookmark: null,
    number: 714,
    img: "https://static.cdnno.com/poster/tan-the-ta-co-the-trong-thay-thanh-mau-giet-quai-roi-bao/150.jpg?1706957067"
  },

  {
    id: 4,
    name: "Xích tâm tuần thiên",
    read: 123,
    number: 2328,
    bookmark: null,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612"
  },
  {
    id: 3,
    name: "Huyền lục",
    read: 201,
    bookmark: null,
    number: 2077,
    img: "https://static.cdnno.com/poster/huyen-luc/150.jpg?1652019253"
  },
  {
    id: 5,
    name: "Lãnh Chúa Cầu Sinh: Từ Tàn Tạ Tiểu Viện Bắt Đầu Công Lược",
    read: 1427,
    number: 1428,
    bookmark: null,
    img: "https://static.cdnno.com/poster/lanh-chua-cau-sinh-tu-tan-ta-tieu-vien-bat-dau-cong-luoc/150.jpg?1622827604"
  },
  {
    id: 2,
    name: "Tận Thế: Ta Có Thể Trông Thấy Thanh Máu, Giết Quái Rơi Bảo",
    read: 215,
    bookmark: null,
    number: 714,
    img: "https://static.cdnno.com/poster/tan-the-ta-co-the-trong-thay-thanh-mau-giet-quai-roi-bao/150.jpg?1706957067"
  },
  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 4431,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },

  {
    id: 3,
    name: "Huyền lục",
    read: 201,
    bookmark: null,
    number: 2077,
    img: "https://static.cdnno.com/poster/huyen-luc/150.jpg?1652019253"
  },
  {
    id: 5,
    name: "Lãnh Chúa Cầu Sinh: Từ Tàn Tạ Tiểu Viện Bắt Đầu Công Lược",
    read: 1427,
    number: 1428,
    bookmark: null,
    img: "https://static.cdnno.com/poster/lanh-chua-cau-sinh-tu-tan-ta-tieu-vien-bat-dau-cong-luoc/150.jpg?1622827604"
  },
  {
    id: 4,
    name: "Xích tâm tuần thiên",
    read: 123,
    number: 2328,
    bookmark: null,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612"
  },

  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 4431,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },
  {
    id: 2,
    name: "Tận Thế: Ta Có Thể Trông Thấy Thanh Máu, Giết Quái Rơi Bảo",
    read: 215,
    bookmark: null,
    number: 714,
    img: "https://static.cdnno.com/poster/tan-the-ta-co-the-trong-thay-thanh-mau-giet-quai-roi-bao/150.jpg?1706957067"
  },
  {
    id: 3,
    name: "Huyền lục",
    read: 201,
    bookmark: null,
    number: 2077,
    img: "https://static.cdnno.com/poster/huyen-luc/150.jpg?1652019253"
  },
  {
    id: 4,
    name: "Xích tâm tuần thiên",
    read: 123,
    number: 2328,
    bookmark: null,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612"
  },
  {
    id: 5,
    name: "Lãnh Chúa Cầu Sinh: Từ Tàn Tạ Tiểu Viện Bắt Đầu Công Lược",
    read: 1427,
    number: 1428,
    bookmark: null,
    img: "https://static.cdnno.com/poster/lanh-chua-cau-sinh-tu-tan-ta-tieu-vien-bat-dau-cong-luoc/150.jpg?1622827604"
  },

  {
    id: 2,
    name: "Tận Thế: Ta Có Thể Trông Thấy Thanh Máu, Giết Quái Rơi Bảo",
    read: 215,
    bookmark: null,
    number: 714,
    img: "https://static.cdnno.com/poster/tan-the-ta-co-the-trong-thay-thanh-mau-giet-quai-roi-bao/150.jpg?1706957067"
  },
  {
    id: 1,
    name: "Vạn Cổ Thần Đế",
    read: 4431,
    bookmark: 4431,
    number: 4431,
    img: "https://static.cdnno.com/poster/van-co-than-de/150.jpg?1585205583"
  },
  {
    id: 5,
    name: "Lãnh Chúa Cầu Sinh: Từ Tàn Tạ Tiểu Viện Bắt Đầu Công Lược",
    read: 1427,
    number: 1428,
    bookmark: null,
    img: "https://static.cdnno.com/poster/lanh-chua-cau-sinh-tu-tan-ta-tieu-vien-bat-dau-cong-luoc/150.jpg?1622827604"
  },
  {
    id: 3,
    name: "Huyền lục",
    read: 201,
    bookmark: null,
    number: 2077,
    img: "https://static.cdnno.com/poster/huyen-luc/150.jpg?1652019253"
  },
  {
    id: 4,
    name: "Xích tâm tuần thiên",
    read: 123,
    number: 2328,
    bookmark: null,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612"
  }
]
const max = listNovel.length / 10 + 1
const data = computed(() => {
  const itemsPerPage = 10
  const startIndex = (current.value - 1) * itemsPerPage
  const endIndex = startIndex + itemsPerPage
  return listNovel.slice(startIndex, endIndex)
})
</script>
