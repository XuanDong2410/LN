<template>
  <q-list class="row">
    <q-item
      v-for="item in listNovel"
      bordered
      class="col-4 b-solid b-b-solid"
      outline
    >
      <div class="img-hover-zoom">
        <q-img :src="item.img" class="w-72px h-96px img-novel" :ratio="1" />
      </div>
      <q-item-section class="row p-3">
        <q-item-label
          lines="1"
          class="text-bold text-14px opacity-80 name-novel mb-2"
          >
          {{ item.name }}
        </q-item-label>

        <q-item-label lines="2" caption>{{ item.describe }} </q-item-label>
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
      </q-item-section>
    </q-item>
  </q-list>
</template>
<script lang="ts" setup>
defineProps<{
  listNovel: {
    value: number
    img: string
    name: string
    author: string
    describe: string
    genre: string
    points: number
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
