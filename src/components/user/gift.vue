<template>
  <q-tabs
    v-model="tab"
    active-color="orange"
    indicator-color="orange"
    align="left"
    class="ml-3"
  >
    <q-tab name="daily" label="Daily" inline-label class="text-capitalize" />
    <q-tab
      name="mission"
      label="Mission"
      inline-label
      class="text-capitalize"
    />
  </q-tabs>

  <q-tab-panels v-model="tab" animated>
    <q-tab-panel name="daily" class="q-pa-none">
      <q-list>
        <q-item class="m-2" v-for="(quest, index) in dailyQuest" :key="index">
          <q-item-section>
            <q-item-label class="text-bold opacity-80">
              {{ quest.name }}
            </q-item-label>
            <q-item-label class="text-caption opacity-70">
              {{ quest.exp }} Exp
            </q-item-label>
          </q-item-section>
          <q-item-section thumbnail>
            <q-btn
              class="w-128px bg-orange text-light-300 p-1 text-12px text-capitalize"
              >Nhận thưởng</q-btn
            >
          </q-item-section>
        </q-item>
        <q-separator />
        <q-item class="m-2">
          <q-item-section>
            <q-item-label class="text-bold opacity-80">
              Xem video quảng cáo
            </q-item-label>
            <q-item-label class="text-caption opacity-70">
              Kẹo ngẫu nhiên
            </q-item-label>
          </q-item-section>
          <q-item-section thumbnail>
            <q-btn
              class="w-128px bg-red-500 text-light-300 p-1 text-12px text-capitalize"
              >Tải App</q-btn
            >
          </q-item-section>
        </q-item>
      </q-list>
      <q-separator />
      <p class="italic opacity-60 m-2 align-text-justify font-sans">
        {{ note }}
      </p>
    </q-tab-panel>
    <q-tab-panel name="mission" class="q-pa-none">
      <q-list>
        <q-item @submit.prevent="simulateSubmit" class="m-2" v-for="(quest, index) in noTimeQuest" :key="index">
          <q-item-section>
            <q-item-label class="text-bold opacity-80">
              {{ quest.name }}
            </q-item-label>
            <q-item-label class="text-caption opacity-70">
              {{ quest.exp }} Exp
            </q-item-label>
          </q-item-section>
          <q-item-section thumbnail>
            <q-btn
              class="w-128px bg-orange text-light-300 p-1 text-12px text-capitalize"
              :loading="submitting"
              @click="quest.done = true"
              >
              Nhận thưởng
              <template #loading>
                <q-spinner-facebook />
              </template>
          </q-btn>
          </q-item-section>
        </q-item>
      </q-list>
      <q-separator />
      <p class="italic opacity-60 m-2 align-text-justify font-sans">
        {{ note }}
      </p>
    </q-tab-panel>
  </q-tab-panels>
</template>

<script lang="ts" setup>
import { ref } from "vue"
const tab = ref("daily")
const note =
  "Đây là nơi để bạn có thể nhận thưởng cho các hoạt động ĐÃ tham gia trong web/app, không khuyến khích vì nhận thưởng mà cố tự tạo ra các hoạt động ảo, hoạt động spam. Tùy vào lịch sử hoạt động của mỗi người sẽ thấy các phần thưởng khác nhau, đừng thắc mắc vì sao người khác có thể nhận thưởng các phần thưởng khác của mình."
const dailyQuest = [
  {
    index: 0,
    name: "Tặng quà cho tác giả hoặc dịch giả",
    done: false,
    exp: 15
  },
  {
    index: 1,
    name: "Đọc 5 chương của một truyện chưa từng đọc",
    done: false,
    exp: 10
  },
  {
    index: 2,
    name: "Thêm 1 bình luận",
    done: false,
    exp: 3
  },
  {
    index: 3,
    name: "Đọc 10 chương truyện",
    done: false,
    exp: 50
  }
]
const noTimeQuest = [
  {
    index: 0,
    name: "Đọc truyện từ các thể loại mới",
    done: false,
    exp: 100
  },
  {
    index: 1,
    name: "Tham gia thảo luận về truyện",
    done: false,
    exp: 100
  },
  {
    index: 2,
    name: "Đọc truyện từ 10 tác giả ",
    done: false,
    exp: 200
  },
  {
    index: 3,
    name: "Đánh giá 10 truyện",
    done: false,
    exp: 500
  }
]
const submitting = ref(false)
function simulateSubmit () {
      submitting.value = true
      console.log(noTimeQuest)
      // Simulating a delay here.
      // When we are done, we reset "submitting"
      // Boolean to false to restore the
      // initial state.
      setTimeout(() => {
        // delay simulated, we are done,
        // now restoring submit to its initial state
        submitting.value = false
      }, 3000)
    }
</script>
