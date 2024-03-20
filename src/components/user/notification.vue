<template>
  <q-list>
    <q-item>
      <q-item-section>
        <q-item-label class="text-18px text-bold">Notification</q-item-label>
      </q-item-section>

      <q-item-section side top>
        <q-chip clickable
          ><q-icon size="1.5em"><i-dashicons-yes /></q-icon
        ></q-chip>
      </q-item-section>
    </q-item>
    <q-separator />
    <q-item v-for="item in displayedNotifications" class="mt-2 mb-2">
      <q-avatar class="mr-3">
        <img :src="item.img" />
      </q-avatar>
      <q-item-section>
        <q-item-label>
          <b>{{ item.name }}</b> vừa thêm <b>{{ item.number }}</b> chương mới
        </q-item-label>
        <q-item-label caption>{{ item.time }}</q-item-label>
      </q-item-section>

      <q-item-section side top>
        <q-icon size="1em" align="center">
          <i-ph-caret-left-fill />
          <q-menu
            transition-show="scale"
            transition-hide="scale"
            anchor="top start"
            self="top right"
            class="m-0"
          >
            <q-list>
              <q-item clickable>
                <q-item-section>
                  <q-item-label lines="1"> Đánh dấu đã đọc</q-item-label>
                </q-item-section>
              </q-item>
              <q-separator />
              <q-item clickable>
                <q-item-section>
                  <q-item-label lines="1">
                    Dừng nhận thông báo này</q-item-label
                  >
                </q-item-section>
              </q-item>
              <q-separator />
              <q-item clickable>
                <q-item-section>Xóa thông báo</q-item-section>
              </q-item>
            </q-list>
          </q-menu></q-icon
        >
      </q-item-section>
      <q-separator />
    </q-item>
    <q-btn v-if="displayLimit < notifications.length" class="bg-yellow-600 text-white w-100%" @click="loadMore">
      Xem thêm
    </q-btn>
    <q-inner-loading :showing="visible">
      <q-spinner-gears size="50px" color="primary" />
    </q-inner-loading>
  </q-list>
</template>
<script lang="ts" setup>
import { ref } from "vue"

const visible = ref(false)

const notifications = [
  {
    index: 1,
    name: "Vạn Cổ Thần Đế",
    number: 2,
    time: "2 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 2,
    name: "Vạn Cổ Thần Đế",
    number: 3,
    time: "3 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 3,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "4 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 4,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "5 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 1,
    name: "Vạn Cổ Thần Đế",
    number: 2,
    time: "2 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 2,
    name: "Vạn Cổ Thần Đế",
    number: 3,
    time: "3 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 3,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "4 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 4,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "5 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 1,
    name: "Vạn Cổ Thần Đế",
    number: 2,
    time: "2 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 2,
    name: "Vạn Cổ Thần Đế",
    number: 3,
    time: "3 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 3,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "4 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 4,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "5 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 1,
    name: "Vạn Cổ Thần Đế",
    number: 2,
    time: "2 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 2,
    name: "Vạn Cổ Thần Đế",
    number: 3,
    time: "3 ngày trước",
    img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/50.jpg?1592316927"
  },
  {
    index: 3,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "4 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  },
  {
    index: 4,
    name: "Toàn Dân Trò Chơi: Từ Zombie Tận Thế Bắt Đầu Treo Máy",
    number: 10,
    time: "5 ngày trước",
    img: "https://static.cdnno.com/user/ba5c1ee4bf41d89c195e01aed64ea6a7/50.jpg?1615709578"
  }
]

const displayLimit = ref(5)

function loadMore() {
  displayLimit.value += 5
}

const displayedNotifications = computed(() => {
  return notifications.slice(0, displayLimit.value)
})
</script>
