<route lang="yaml">
name: "novel-chap"
</route>

<template>
  <div class="row m-auto">
    <div
      class="col-10 offset-md-1 py-10 d-flex justify-center"
      @click="close()"
    >
      <q-card class="p-2 pb-4">
        <!-- <q-toolbar>
          <q-btn class="w-30">
            <i-cil-arrow-left class="size-1.5em" />
          </q-btn>
          <q-space />
          <q-btn class="w-30"><i-cil-arrow-right class="size-1.5em" /></q-btn>
        </q-toolbar> -->
        <q-item>
          <q-item-label class="text-h4"
            >{{ chap }}{{ data.nameChap }}</q-item-label
          >
        </q-item>
        <q-item>
          <q-item-label caption>
            <q-chip class="bg-white" clickable
              ><i-solar-book-2-bold class="m-0.5" />{{ data.nameNovel }}</q-chip
            >
            <q-chip class="bg-white" clickable
              ><i-mdi-book-edit class="m-0.5" />{{ data.nameAuthor }}</q-chip
            >
            <q-chip class="bg-white" clickable
              ><i-solar-text-outline class="m-0.5" />{{ data.word }} chữ</q-chip
            >
            <q-chip class="bg-white" clickable
              ><i-mdi-heart class="m-0.5" />{{ data.react }} cảm xúc</q-chip
            >
            <q-chip class="bg-white" clickable
              ><i-mdi-clock class="m-0.5" />{{ data.time }}</q-chip
            >
          </q-item-label>
        </q-item>
        <q-item-section>
          <p class="text-20px">{{ data.content }}</p>
        </q-item-section>
        <q-item-section>
          <h6>==============</h6>
          <q-space />
          <q-toolbar class="row text-body2 text-center">
            <div class="col-2 offset-md-3 d-flex justify-center">
              <i-noto:star class="size-2.25em mx-auto" clickable />
              <h6>Đánh giá</h6>
            </div>
            <div class="col-2">
              <i-noto:white-flower class="size-2.4em mx-auto" clickable />
              <h6>Đề cử</h6>
            </div>
            <div class="col-2">
              <i-noto-wrapped-gift class="size-2em mx-auto" clickable />
              <h6>Tặng quà</h6>
              <hr />
            </div>
          </q-toolbar>
        </q-item-section>
      </q-card>
      <!-- <q-btn-toggle
        v-model="model"
        push
        glossy
        spread
        toggle-color="teal"
        class="my-custom-toggle mt-2"
        no-caps
        rounded
        color="white"
        text-color="primary"
        :options="[
          { value: 'one', slot: 'one' },
          { value: 'two', slot: 'two' },
          { value: 'three', slot: 'three' }
        ]"
      >
        <template #one>
          <div class="row items-center no-wrap">
            <i-cil-arrow-left class="size-2.5em" />
          </div>
        </template>

        <template #two>
          <div class="row items-center no-wrap">
            <q-icon name="report" size="2em" />
          </div>
        </template>

        <template #three>
          <div class="row items-center no-wrap">
            <i-cil-arrow-right class="size-2.5em" />
          </div>
        </template>
      </q-btn-toggle> -->
    </div>

    <!-- <div class="col-1 fixed right-5% mt-3">
      <q-btn-group class="column">
        <q-btn class="m-1"
          ><i-akar-icons:three-line-horizontal class="size-2.5em" />
          <q-tooltip anchor="center right" self="center start">
            <h6>Danh sách chương</h6>
          </q-tooltip>
        </q-btn>
        <q-btn>
          <i-noto-back-arrow class="size-2em" />
          <q-tooltip anchor="center right" self="center start">
            <h6>Thông tin truyện</h6>
          </q-tooltip>
        </q-btn>
        <q-btn>
          <i-noto-red-exclamation-mark class="size-2em" />
          <q-tooltip anchor="center right" self="center start">
            <h6>Hướng dẫn</h6>
          </q-tooltip>
          <q-menu fit anchor="top left" self="top end">
            <q-item clickable>
              <q-item-section>New tab</q-item-section>
            </q-item>
            <q-item clickable>
              <q-item-section>New incognito tab</q-item-section>
            </q-item>
          </q-menu>
        </q-btn>
      </q-btn-group>
    </div>
    <div class="col-1 fixed right-5% bottom-20%">
      <q-btn-group class="col self-end column mt-4 absolute bottom-0">
        <q-btn class="mb-2" round>
          <q-fab padding="0" direction="up" class="mb-1">
            <template #icon>
              <q-icon size="2em">
                <i-noto-enraged-face class="size-1.5em" />
              </q-icon>
            </template>
            <q-fab-action>
              <i-noto-enraged-face class="size-2.5em" />
            </q-fab-action>
            <q-fab-action>
              <i-noto-crying-face class="size-2.5em" />
            </q-fab-action>
            <q-fab-action class="column">
              <i-noto-face-with-tears-of-joy class="size-2.5em" clickable />
            </q-fab-action>
            <q-fab-action>
              <i-noto-thumbs-up-medium-light-skin-tone class="size-2.5em" />
            </q-fab-action>
            <q-fab-action>
              <i-fluent-emoji-flat-red-heart class="size-2.5em" />
            </q-fab-action>
          </q-fab>
        </q-btn>
        <q-btn>
          <i-noto-bookmark-tabs class="size-2em" />
          <q-tooltip anchor="center right" self="center start">
            <h6>BookMark</h6>
          </q-tooltip>
        </q-btn>
        <q-btn>
          <i-noto-writing-hand-medium-light-skin-tone class="size-2em" />
          <q-tooltip anchor="center right" self="center start">
            <h6>Comment</h6>
          </q-tooltip>
        </q-btn>
      </q-btn-group>
    </div> -->
    <div class="col-2 fixed-bottom-right mb-5 text-center">
      <q-btn @click="open()" class="opacity-60 capitalize">
        <i-akar-icons:three-line-horizontal class="size-1.5em m-0.1" />
        Hiện thanh công cụ
      </q-btn>
    </div>
  </div>
  <q-dialog v-model="dialog" position="bottom" seamless full-width>
    <q-card class="bg-gray-300">
      <q-toolbar>
        <q-btn-group outline rounded class="b-gray-400">
          <q-btn flat @click="minus()">
            <q-icon><i-ic:baseline-minus /></q-icon>
          </q-btn>
          <q-btn>{{ percent }}%</q-btn>
          <q-btn flat @click="plus()">
            <q-icon><i-ic:baseline-plus /></q-icon>
          </q-btn>
        </q-btn-group>
        <q-chip dense class="transparent">{{ percent }}/ 100%</q-chip>
        <q-linear-progress
          dark
          stripe
          rounded
          size="10px"
          :value="percent"
          color="red"
          class="q-mt-sm w-30%"
        />
        <q-btn rounded unelevated class="capitalize">
          Trước
          <q-tooltip
            anchor="top middle"
            self="center middle"
            class="text-light-400 bg-dark-300 text-14px"
          >
            Chương trước!
          </q-tooltip>
        </q-btn>
        <q-btn rounded unelevated class="capitalize">
          Sau
          <q-tooltip
            anchor="top middle"
            self="center middle"
            class="text-light-400 bg-dark-300 text-14px"
          >
            Chương sau!
          </q-tooltip>
        </q-btn>
        <q-btn rounded unelevated class="capitalize">Chương</q-btn>
        <q-btn rounded unelevated class="capitalize">
          <q-icon><i-ep:setting /></q-icon>
          Cài đặt
        </q-btn>
        <q-btn rounded unelevated class="capitalize">
          <q-icon><i-material-symbols-light-comment-outline-rounded /></q-icon>
          Bình luận</q-btn
        >
        <q-btn rounded unelevated class="capitalize">
          <q-icon><i-solar:heart-outline /></q-icon>
          Yêu thích
        </q-btn>
        <q-btn rounded unelevated class="capitalize">
          <q-icon><i-material-symbols-light-zoom-out-map-rounded /></q-icon>
          Phóng to
        </q-btn>
      </q-toolbar>
    </q-card>
  </q-dialog>
</template>
<script lang="ts" setup>
import { ref } from "vue"

defineProps<{
  novel: string
  chap: string
  datas: {
    nameChap: string
    nameNovel: string
    nameAuthor: string
    word: string
    react: string
    time: string
    content: string
  }
}>()

const dialog = ref(false)
function open() {
  dialog.value = true
}
function close() {
  dialog.value = false
}
const percent = computed(() => {
  return 0.3
})
function minus() {
  return percent
}
function plus() {
  return percent
}

const model = ref("two-model")

const data = {
  nameChap: "Chương 4175: Tức giận",
  nameNovel: "Vạn cổ thần đế",
  nameAuthor: "DarkHero",
  word: 1724,
  react: 13,
  time: "2024-01-26 09:10:12",
  content:
    "Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp. Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp. Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp. Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp. Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp.Diêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn phápDiêm Vô Thần . Quanh nguời, xuất hiện vạn đạo phân thân. Vạn đạo phân thân, đồng thời tu tập vạn pháp"
}
</script>
