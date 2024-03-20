<template>
  <div class="q-pa-md w-100% m-auto row">
    <div class="col-8">
      <div class="text-h6 text-bold opacity-70">Đánh giá cao</div>
      <q-list class="row">
        <q-item
          v-for="item in votes"
          bordered
          class="col-6 b-solid b-b-solid"
          outline
        >
          <div class="img-hover-zoom py-2">
            <q-img :src="item.img" class="w-72px h-96px img-novel" :ratio="1" />
          </div>
          <q-item-section class="row p-2">
            <q-item-label
              lines="1"
              class="text-bold text-13px opacity-90 name-novel"
            >
              {{ item.name }}
              <q-tooltip anchor="center end" self="center end">
                {{ item.name }}
              </q-tooltip>
            </q-item-label>
            <div class="text-green-700 m-2">
              <q-chip class="bg-red-500 text-white text-bold">
                {{ item.vote_point }}
              </q-chip>
              {{ item.numbers }} đánh giá
            </div>
            <q-item-label lines="2" caption>
              {{ item.describe }}
            </q-item-label>
            <q-item class="w-100% m-0 p-0">
              <q-item-section>
                <q-item-label caption lines="1">
                  <q-icon class="mr-0.5 mb-0.5">
                    <i-mdi-user-edit />
                  </q-icon>
                  {{ item.author }}
                </q-item-label>
              </q-item-section>
              <q-item-section side>
                <q-chip
                  square
                  outline
                  side
                  class="b-yellow-500 b-solid bg-white text-yellow-500 text-10px text-center"
                >
                  {{ item.genre }}
                </q-chip>
              </q-item-section>
            </q-item>
            <q-separator />
          </q-item-section>
        </q-item>
      </q-list>
    </div>
    <div class="col-4">
      <div class="text-h6 text-bold opacity-70">Mới đánh giá</div>
      <q-list>
        <q-item v-for="item in feedBacks" class="bg-gray-100 m-1" clickable>
          <q-avatar class="mr-2">
            <q-img :src="item.img" />
          </q-avatar>
          <q-item-section class="ml-1">
            <q-item-label class="opacity-75">
              <b>{{ item.user }}</b> đánh giá
            </q-item-label>
            <q-item-label class="text-red-600 text-bold">{{
              item.novel
            }}</q-item-label>
            <q-item-label class="text-body2 opacity-75" lines="3">
              {{ item.describe }}
            </q-item-label>
          </q-item-section>
          <q-item-section side top>
            <q-chip class="bg-red-500 text-bold text-white">
              {{ item.vote_point }}
            </q-chip>
          </q-item-section>
        </q-item>
      </q-list>
    </div>
  </div>
</template>
<script lang="ts" setup>
defineProps<{
  votes:   {
    value: number
    img: string
    name: string
    author: string
    describe: string
    genre: string
    vote_point: string
    numbers: number
  }[]
  feedBacks: {
    user: string,
    img: string,
    novel: string,
    vote_point: string,
    describe: string
  }[]
}>()


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
