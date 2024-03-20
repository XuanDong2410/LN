<template>
  <div class="q-pa-md">
    <q-list bordered class="rounded-borders">
      <q-expansion-item
        :content-inset-level="0.5"
        v-for="book in books"
        icon="book"
        :label="book.name"
        class="text-capitalize mb-3"
        default-opened
      >
        <div class="row">
          <div class="col-2">
            <q-img
              :src="book.img"
              class="rounded-1em opacity-90"
              :ratio="3 / 4"
            />
          </div>
          <div class="col-10" hover="text-blue-300">
            <!-- <q-scroll-area class="w-100% h-70 ml-5" :offset="250"> -->
            <q-btn
              unelevated
              v-for="chap in book.chap"
              class="w-90% text-capitalize"
              clickable
            >

              <div align="left" class="col-12 col-md-6 d-flex left">

                <q-icon :name="chap.icon" class="size-0.em" />
                <h7 class="align-start">Chương {{ chap.id }} :</h7>

                <h7 class="align-start">{{ chap.name }}</h7>
              </div>

              <h7 class="col-12 col-md-4">{{ chap.time }}</h7>
            </q-btn>
            <!-- </q-scroll-area> -->
          </div>
        </div>
      </q-expansion-item>
    </q-list>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue"

const books = ref([
  {
    id: 1,
    name: "Tập 1",
    numbers: 20,
    img: "https://i2.docln.net/ln/series/covers/s16947-c88762a7-3ee0-494f-9f6e-4ed58d143d8d.jpg",
    chap: [
      {
        id: 1,
        idbook: 1,
        name: "Tám trăm năm sau ",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 2,
        idbook: 1,
        name: "Mở ra Thần Võ Ấn Ký",
        time: "1-24-2020",
        icon: ""
      },
      { id: 3, idbook: 1, name: "Hoàng Cực Cảnh", time: "1-24-2020", icon: "" },
      {
        id: 4,
        idbook: 2,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 5,
        idbook: 3,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 1,
        idbook: 1,
        name: "Tám trăm năm sau",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 2,
        idbook: 1,
        name: "Mở ra Thần Võ Ấn Ký",
        time: "1-24-2020",
        icon: ""
      },
      { id: 3, idbook: 1, name: "Hoàng Cực Cảnh", time: "1-24-2020", icon: "" },
      {
        id: 4,
        idbook: 2,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 5,
        idbook: 3,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 1,
        idbook: 1,
        name: "Tám trăm năm sau",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 2,
        idbook: 1,
        name: "Mở ra Thần Võ Ấn Ký",
        time: "1-24-2020",
        icon: ""
      },
      { id: 3, idbook: 1, name: "Hoàng Cực Cảnh", time: "1-24-2020", icon: "" },
      {
        id: 4,
        idbook: 2,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 5,
        idbook: 3,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 1,
        idbook: 1,
        name: "Tám trăm năm sau",
        time: "1-24-2020",
        icon: "photo"
      },
      {
        id: 2,
        idbook: 1,
        name: "Mở ra Thần Võ Ấn Ký",
        time: "1-24-2020",
        icon: ""
      },
      { id: 3, idbook: 1, name: "Hoàng Cực Cảnh", time: "1-24-2020", icon: "" },
      {
        id: 4,
        idbook: 2,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 5,
        idbook: 3,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: "photo"
      }
    ]
  },
  {
    id: 2,
    name: "Tập 2",
    numbers: 20,
    img: "https://i2.docln.net/ln/series/covers/s16947-c88762a7-3ee0-494f-9f6e-4ed58d143d8d.jpg",
    chap: [
      {
        id: 1,
        idbook: 1,
        name: "Tám trăm năm sau",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 2,
        idbook: 1,
        name: "Mở ra Thần Võ Ấn Ký",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 4,
        idbook: 2,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: ""
      },
      {
        id: 5,
        idbook: 3,
        name: "Thời Không Bí Điển",
        time: "1-24-2020",
        icon: "photo"
      }
    ]
  },
  {
    id: 3,
    name: "Tập 3",
    numbers: 20,
    img: "https://i2.docln.net/ln/series/covers/s16947-c88762a7-3ee0-494f-9f6e-4ed58d143d8d.jpg"
  }
])
</script>
