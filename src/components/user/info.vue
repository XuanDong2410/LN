<template>
  <q-card class="w-80% m-auto" flat>
    <!-- <div class="text-h5 m-2 opacity-80 text-bold">Account</div> -->

    <q-list class="max-w-170">
      <q-item>
        <q-avatar class="size-2em">
          <q-img
            src="https://static.cdnno.com/user/7b6ca64c0381d9743781acfc797c8ba6/100.jpg?1642616770"
          />
        </q-avatar>
        <q-item-section class="ml-2">
          <q-item-label class="text-bold text-opacity-80 text-16px">
            {{ nickname }}
            <q-chip class="bg-orange-500 text-white"
              >Lv.{{ currentLevel?.index }}</q-chip
            >
          </q-item-label>
          <q-item-label text-caption>3 năm trước</q-item-label>
          <q-popup-edit
            v-model="nickname"
            :validate="(val) => val.length > 5"
            v-slot="scope"
          >
            <q-input
              autofocus
              dense
              v-model="scope.value"
              counter
              maxlength="18"
              hint="Name"
              :rules="[
                (val) => scope.validate(val) || 'More than 5 chars required'
              ]"
            >
              <template #after>
                <q-btn
                  flat
                  dense
                  color="negative"
                  icon="cancel"
                  @click.stop.prevent="scope.cancel"
                />

                <q-btn
                  flat
                  dense
                  color="positive"
                  icon="check_circle"
                  @click.stop.prevent="scope.set"
                  :disable="
                    scope.validate(scope.value) === false ||
                    scope.initialValue === scope.value
                  "
                />
              </template>
            </q-input>
          </q-popup-edit>
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section class="m-auto">
          {{ description }}
          <q-popup-edit
            v-model="description"
            :validate="(val) => val.length > 5"
            v-slot="scope"
          >
            <q-input
              autofocus
              dense
              v-model="scope.value"
              counter
              maxlength="50 "
              hint="Description"
              :rules="[
                (val) => scope.validate(val) || 'More than 5 chars required'
              ]"
            >
              <template #after>
                <q-btn
                  flat
                  dense
                  color="negative"
                  icon="cancel"
                  @click.stop.prevent="scope.cancel"
                />

                <q-btn
                  flat
                  dense
                  color="positive"
                  icon="check_circle"
                  @click.stop.prevent="scope.set"
                  :disable="
                    scope.validate(scope.value) === false ||
                    scope.initialValue === scope.value
                  "
                />
              </template>
            </q-input>
          </q-popup-edit>
        </q-item-section>
      </q-item>
      <q-item>
        <q-linear-progress
          rounded
          size="20px"
          :value="level"
          color="warning"
          class="q-mt-sm"
        >
        </q-linear-progress>
      </q-item>
      <q-item class="flex flex-center transparent">
        <q-chip color="warning" text-color="white" :label="exp" />
      </q-item>

      <q-separator />
      <q-item>
        <q-item-section>
          <q-item-label>Level</q-item-label>
        </q-item-section>
        <q-item-section class="text-bold">
          {{ currentLevel?.name }}
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section>
          <q-item-label>Read</q-item-label>
        </q-item-section>
        <q-item-section>
          <h6>
            <b> {{ readNovel }} </b> Novels
          </h6>
          <h6>
            <b> {{ readChap }} </b> Chaps
          </h6>
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section>
          <q-item-label>Comment</q-item-label>
        </q-item-section>
        <q-item-section class="text-bold">
          {{ comments }}
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section>
          <q-item-label>Favorites</q-item-label>
        </q-item-section>
        <q-item-section class="text-bold">
          {{ favorites }}
        </q-item-section>
      </q-item>
      <q-item>
        <q-item-section></q-item-section>
        <q-item-section side top>
          <q-btn color="orange" label="Update" class="m-3" align="center" />
        </q-item-section>
      </q-item>
    </q-list>
  </q-card>
</template>

<script lang="ts" setup>
import { ref } from "vue"

const nickname = ref("Đào Xuân Đông")
const description = ref("I am a student")
const Listlevel = [
  { index: 1, exp: 100, name: "Phàm nhân" },
  { index: 2, exp: 200, name: "Luyện Khí Tầng Một" },
  { index: 3, exp: 300, name: "Luyện Khí Tầng Hai" },
  { index: 4, exp: 400, name: "Luyện Khí Tầng Ba" },
  { index: 5, exp: 500, name: "Luyện Khí Tầng Bốn" },
  { index: 6, exp: 600, name: "Luyện Khí Tầng Năm" },
  { index: 7, exp: 700, name: "Luyện Khí Tầng Sáu" },
  { index: 8, exp: 800, name: "Luyện Khí Tầng Bảy" },
  { index: 9, exp: 900, name: "Luyện Khí Tầng Tám" },
  { index: 10, exp: 1000, name: "Luyện Khí Tầng Chín" },
  { index: 11, exp: 2000, name: "Trúc Cơ Sơ Kỳ" },
  { index: 12, exp: 3000, name: "Trúc Cơ Trung Kỳ" },
  { index: 13, exp: 4000, name: "Trúc Cơ Hậu Kỳ" },
  { index: 14, exp: 5000, name: "Kết Đan Sơ Kỳ" },
  { index: 15, exp: 10000, name: "Kết Đan Trung Kỳ" },
  { index: 16, exp: 15000, name: "Kết Đan Hậu Kỳ" },
  { index: 17, exp: 20000, name: "Nguyên Anh Sơ Kỳ" },
  { index: 18, exp: 30000, name: "Nguyên Anh Trung Kỳ" },
  { index: 19, exp: 40000, name: "Nguyên Anh Hậu Kỳ" },
  { index: 20, exp: 50000, name: "Hóa Thần Sơ Kỳ" },
  { index: 21, exp: 75000, name: "Hóa Thần Trung Kỳ" },
  { index: 22, exp: 100000, name: "Hóa Thần Hậu Kỳ" },
  { index: 23, exp: 200000, name: "Luyện Hư Sơ Kỳ" },
  { index: 24, exp: 300000, name: "Luyện Hư Trung Kỳ" },
  { index: 25, exp: 400000, name: "Luyện Hư Hậu Kỳ" },
  { index: 26, exp: 500000, name: "Hợp Thể Sơ Kỳ" },
  { index: 27, exp: 750000, name: "Hợp Thể Trung Kỳ" },
  { index: 28, exp: 1000000, name: "Hợp Thể Hậu Kỳ" },
  { index: 29, exp: 2000000, name: "Đại Thừa Sơ Kỳ" },
  { index: 30, exp: 3000000, name: "Đại Thừa Trung Kỳ" },
  { index: 31, exp: 4000000, name: "Đại Thừa Hậu Kỳ" },
  { index: 32, exp: 5000000, name: "Chân Tiên Sơ Kỳ" },
  { index: 33, exp: 7500000, name: "Chân Tiên Trung Kỳ" },
  { index: 34, exp: 10000000, name: "Chân Tiên Hậu Kỳ" },
  { index: 35, exp: 20000000, name: "Hư Linh Sơ Kỳ" },
  { index: 36, exp: 30000000, name: "Hư Linh Trung Kỳ" },
  { index: 37, exp: 40000000, name: "Hư Linh Hậu Kỳ" },
  { index: 38, exp: 50000000, name: "Đại La Sơ Kỳ" },
  { index: 39, exp: 75000000, name: "Đại La Trung Kỳ" },
  { index: 40, exp: 90000000, name: "Đại La Hậu Kỳ" },
  { index: 41, exp: 99999999, name: "Tiên Vương" }
]

const currentExp = ref(30)
function calcLevel(currentExp: number) {
  const currentLevel = Listlevel.find((item) => item.exp > currentExp - 1)
  if (!currentLevel) {
    return Listlevel[0]
  }
  return currentLevel
}
const currentLevel = Listlevel.find(
  (item) => item.index === calcLevel(currentExp.value)?.index ?? 1
)

function calcExp() {
  return String("Exp : " + currentExp.value + "/" + currentLevel?.exp)
}
const cur = currentLevel ?? Listlevel[2]
function calcPercentLevel() {
  if (currentExp.value < Listlevel[0].exp) {
    return currentExp.value / cur.exp
  }
  return (
    (currentExp.value - Listlevel[cur.index - 2].exp) /
    (cur.exp - Listlevel[cur.index - 2].exp)
  )
}
const level = calcPercentLevel()
const exp = calcExp()

const readChap = 12961
const readNovel = 51
const comments = 6
const favorites = 123
</script>
