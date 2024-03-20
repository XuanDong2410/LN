<template>
  <q-page class="d-flex justify-center">
    <q-card class="w-80% m-auto pb-10">
      <q-toolbar class="d-flex justify-end">
        <q-btn text unelevated rounded class="text-black" no-caps>
          Xếp hạng : <b> {{ menuSelect }}</b>
          <!-- <Component :is="menu.icon" class="size-1em ml-1" /> -->
          <q-menu
            anchor="bottom end"
            self="top end"
            transition-show="jump-down"
            transition-hide="jump-up"
          >
            <q-list style="min-width: 100px">
              <q-item v-for="item in menu" clickable>
                <q-item-section @click="menuSelect = item.name">
                  {{ item.name }}
                </q-item-section>
              </q-item>
            </q-list>
          </q-menu>
          <i-tabler-caret-down-filled />
        </q-btn>
      </q-toolbar>
      <q-splitter v-model="splitterModel" active-bg-color="bg-yellow-300">
        <template #before>
          <q-tabs
            :width="10"
            v-model="tab"
            vertical
            active-color="black"
            indicator-color="orange"
            active-bg-color="yellow-500"
            class="capitalize"
          >
            <q-tab
              v-for="rank in listRank"
              :name="rank.name"
              class="capitalize m-1"
            >
              <Component :is="rank.icon" class="size-1.5em" />
              {{ rank.label }}
            </q-tab>
          </q-tabs>
        </template>

        <template #after>
          <q-tab-panels v-model="tab" animated>
            <q-tab-panel
              v-for="rank in listRank"
              :name="rank.name"
              :label="rank.label"
              class="q-pa-none"
            >
              <Component
                :is="Rank"
                :data="Read"
                :icon="rank.icon"
                :react="rank.typeReact"
              />
            </q-tab-panel>
          </q-tab-panels>
        </template>
      </q-splitter>
    </q-card>
  </q-page>
</template>
<script lang="ts" setup>
import { ref } from "vue"

import Rank from "../components/rank.vue"
import Read from "../data/rank/read.json"

import topIcon from "~icons/mdi/arrow-top-circle-outline"
import readIcon from "~icons/mdi/book-open-page-variant"
import discussIcon from "~icons/mdi/comment-question-outline"
import giftIcon from "~icons/mdi/gift"
import favoriteIcon from "~icons/mdi/heart-outline"
import voteIcon from "~icons/mdi/vote"
const splitterModel = ref(15)
const tab = ref("index")

/// TABS
const listRank = [
  {
    name: "index",
    label: "Thịnh hành",
    icon: topIcon,
    value: Read,
    typeReact: "index"
  },
  {
    name: "read",
    label: "Đọc nhiều",
    icon: readIcon,
    value: Read,
    typeReact: "read"
  },
  {
    name: "gift",
    label: "Tặng thưởng",
    icon: giftIcon,
    value: Read,
    typeReact: "gift"
  },
  {
    name: "vote",
    label: "Đề cử",
    icon: voteIcon,
    value: Read,
    typeReact: "vote"
  },
  {
    name: "favorite",
    label: "Yêu thích",
    icon: favoriteIcon,
    value: Read,
    typeReact: "favorite"
  },
  {
    name: "discuss",
    label: "Thảo luận",
    icon: discussIcon,
    value: Read,
    typeReact: "discuss"
  }
]

const menu = computed(() => [
  {
    name: "Theo ngày"
  },
  {
    name: "Theo tuần"
  },
  {
    name: "Theo tháng"
  }
])
const menuSelect = ref("Theo tuần")
</script>
<style>
.img-novel {
  box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.3);
}
</style>
