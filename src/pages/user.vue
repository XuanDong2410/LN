<template>
  <q-page class="d-flex justify-center">
    <q-card class="w-80% m-auto p-10">
      <q-splitter v-model="splitterModel" active-bg-color="bg-yellow-300">
        <template #before>
          <q-tabs
            v-model="tab"
            vertical
            active-color="black"
            indicator-color="orange"
            active-bg-color="yellow-300"
          >
            <q-tab
              v-for="{ index, name } in infors"
              :key="name"
              :name="index"
              :label="name"
              dense
              inline-label
              class="text-capitalize"
            >
            </q-tab>
          </q-tabs>
        </template>

        <template #after>
          <q-tab-panels v-model="tab" animated>
            <q-tab-panel
              v-for="{ index, name, value } in infors"
              :name="index"
              :label="name"
              class="q-pa-none"
            >
              <component :is="value" />
            </q-tab-panel>
          </q-tab-panels>
        </template>
      </q-splitter>
    </q-card>
  </q-page>
</template>
<script lang="ts" setup>
import Bookcase from "src/components/user/bookcase.vue"
import { ref } from "vue"

import Gift from "../components/user/gift.vue"
import Helps from "../components/user/helps.vue"
import Profile from "../components/user/info.vue"
import Notification from "../components/user/notification.vue"
import Setting from "../components/user/setting.vue"
//  import UserNovel from "../components/user/user_novel.vue"
const tab = ref(1)
const splitterModel = ref(20)
const infors = [
  {
    index: 1,
    name: "Hồ sơ",
    icon: "",
    value: Profile
  },
  {
    index: 2,
    name: "Tủ truyện",
    icon: "",
    value: Bookcase
  },
  {
    index: 3,
    name: "Cài đặt",
    icon: "",
    value: Setting
  },
  // {
  //   index: 4,
  //   name: "Tài sản",
  //   icon: "",
  //   value: ["Kẹo", "Hoa"]
  // },
  // {
  //   index: 5,
  //   name: "Mua kẹo",
  //   icon: "",
  //   value: null
  // },
  // {
  //   index: 6,
  //   name: "Nâng cấp",
  //   icon: "",
  //   value: null
  // },
  {
    index: 7,
    name: "Nhận thưởng",
    icon: "",
    value: Gift
  },
  {
    index: 8,
    name: "Thông báo",
    icon: "",
    value: Notification
  },
  {
    index: 9,
    name: "Trợ giúp & Báo lỗi",
    icon: "",
    value: Helps
  }
]
</script>
