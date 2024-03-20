<template>
  <div class="row">
    <div class="col-8 relative">
      <div class="m-2">
        <div class="cursor-pointer text-blue-600 mt-3">
          {{ numberCommet }}<b> Bình luận</b>
        </div>

        <!-- <q-space /> -->
        <!-- <q-btn dense class="bg-white"> -->
        <q-select
          filled
          v-model="model"
          :options="options"
          option-value="id"
          option-label="desc"
          option-disable="inactive"
          emit-value
          map-options
          label-color="blue"
          class="h-1em w-10em m-0 absolute right-0 top-0"
        />
      </div>
      <div class="mt-10 m-3">
        <q-input
          outlined
          bottom-slots
          v-model="text"
          label="Bình luận"
          counter
          :dense="dense"
          rounded
          autogrow
        >
          <template #before>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar5.jpg" />
            </q-avatar>
          </template>

          <template #append>
            <q-icon
              v-if="text !== ''"
              name="close"
              @click="text = ''"
              class="cursor-pointer"
            />
          </template>
          <template #after>
            <q-btn round dense flat icon="send" />
          </template>
        </q-input>
      </div>
      <q-separator />
      <div class="mt-10 m-3">
        <q-card v-for="comment in comments" class="m-3">
          <q-item>
            <q-item-section avatar>
              <div class="relative inline-block">
                <q-avatar size="60px">
                  <q-img :src="comment.user.img" />
                </q-avatar>
                <div
                  class="py-1px leading-normal px-1.3 text-13px min-w-0 rounded-xl bg-yellow-600 whitespace-nowrap absolute bottom--0 py-0 text-white left-1/2 translate-x--1/2"
                >
                  Cấp {{ comment.user.level }}
                </div>
              </div>
            </q-item-section>

            <q-item-section>
              <q-item-label class="ml-4">{{ comment.user.name }}</q-item-label>
              <q-chip class="opacity-90 bg-white">
                <i-mdi-clock class="mr-1" />
                <h6 class="text-caption">{{ comment.date }}</h6>
                <i-akar-icons-glasses class="size-1.5em mr-1 ml-1" />
                <h6 class="text-caption">Chương {{ comment.chaps }}</h6>
              </q-chip>
            </q-item-section>
          </q-item>

          <q-item>
            <q-card-section>{{ comment.content }}</q-card-section>
          </q-item>
          <q-item class="row mb-3">
             <div class="col-6">
              <h6 class="text-caption italic text-14px ml-4">{{ comment.replys.length }} phản hồi </h6>
              <!--<q-expansion-item :label="comment.replys.length.toString()">
                <q-separator />
                <q-card>
                  <q-card-section>
                    <q-card v-for="reply in comment.replys" class="m-3">
                      <q-item>
                        <q-item-section avatar>
                          <div class="relative inline-block">
                            <q-avatar size="65px">
                              <q-img :src="reply.user.img" />
                            </q-avatar>
                            <div
                              class="py-1px leading-normal px-1.3 text-13px min-w-0 rounded-xl bg-yellow-600 whitespace-nowrap absolute bottom--0 py-0 text-white left-1/2 translate-x--1/2"
                            >
                              Cấp {{ reply.user.level }}
                            </div>
                          </div>
                        </q-item-section>

                        <q-item-section>
                          <q-item-label class="ml-4">{{
                            reply.user.name
                          }}</q-item-label>
                          <q-chip class="opacity-90 bg-white">
                            <i-mdi-clock class="mr-1" />
                            <h6 class="text-caption">{{ reply.date }}</h6>
                          </q-chip>
                        </q-item-section>
                      </q-item>

                      <q-item>
                        <q-card-section>{{ reply.content }}</q-card-section>
                      </q-item>
                      <div class="row mb-3">
                        <div class=""></div>
                        <div class="d-flex opacity-95 bg-white">
                          <q-chip
                            round
                            dense
                            flat
                            icon="thumb_up"
                            size="11px"
                            class="text-14px"
                            clickable
                          >
                            <h6>{{ reply.like }}</h6>
                          </q-chip>
                          <q-chip
                            round
                            dense
                            flat
                            icon="reply"
                            size="12px"
                            class="ml-3 text-capitalize text-14px"
                            clickable
                            ><h6>Phản hồi</h6>
                          </q-chip>

                          <q-chip
                            round
                            dense
                            flat
                            icon="flag"
                            size="12px"
                            class="ml-3 text-capitalize text-14px"
                            clickable
                            ><h6>Báo xấu</h6>
                          </q-chip>
                        </div>
                      </div>
                    </q-card>
                  </q-card-section>
                </q-card>
              </q-expansion-item>-->
            </div>

            <div class="col-6 d-flex justify-center opacity-95 bg-white">
              <q-chip
                round
                dense
                flat
                icon="thumb_up"
                size="11px"
                class="text-14px"
                clickable
              >
                <h6>{{ comment.like }}</h6>
              </q-chip>
              <q-chip
                round
                dense
                flat
                icon="reply"
                size="12px"
                class="ml-3 text-capitalize text-14px"
                clickable
                @click="showCommentForm = !showCommentForm"
                ><h6>Phản hồi</h6>
              </q-chip>

              <q-chip
                round
                dense
                flat
                icon="flag"
                size="12px"
                class="ml-3 text-capitalize text-14px"
                clickable
                ><h6>Báo xấu</h6>
              </q-chip>
            </div>

          </q-item>
          <q-item v-if="showCommentForm">
            <div class="w-100%" >
              <div class="col-12 ">
                <q-input
                  outlined
                  bottom-slots
                  v-model="text"
                  label="Bình luận"
                  :dense="dense"
                  rounded
                  autogrow
                >
                  <template #before>
                    <q-avatar class="size-1.5em">
                      <q-img src="https://cdn.quasar.dev/img/avatar5.jpg"  />
                    </q-avatar>
                  </template>


                  <template #after>
                    <q-btn round dense flat icon="send" />
                  </template>
                </q-input>
              </div>
            </div>
          </q-item>
        </q-card>
        <q-separator />
      </div>
    </div>
    <div class="col-4">
      <h3 class="opacity-90 text-medium-400">Lưu ý khi bình luận</h3>
      <q-item class="opacity-80" v-for="note in notes"
        >{{ note.number }}. {{ note.content }}</q-item
      >
      <p class="mt-3 opacity-80 italic">
        Vui lòng xem và tuân theo đầy đủ các quy định tại Điều Khoản Dịch Vụ khi
        sử dụng website
      </p>
    </div>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue"
const numberCommet = ref(78809)
const model = ref("Mới nhất")
const text = ref("")
const dense = ref(false)

const showCommentForm = ref(false)
const options = [
  {
    id: 1,
    desc: "Mới nhất"
  },
  {
    id: 2,
    desc: "Cũ nhất"
  },
  {
    id: 3,
    desc: "Lượt thích"
  }
]
const comments = [
  {
    id: 1,
    user: {
      name: "Nguyen Van A",
      img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
      level: 4
    },
    content: "Truyện hay",
    date: "2021-01-01",
    chaps: 4173,
    like: 100,
    replys: [
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "hay",
        date: "2021-01-01 12:00:00",
        like: 100
      },
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện",
        date: "2021-01-01 12:00:00",
        like: 100
      }
    ]
  },
  {
    id: 7,
    user: {
      name: "Nguyen A",
      img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
      level: 4
    },
    content: "Truyện hay",
    date: "2021-01-01",
    chaps: 4173,
    like: 100,
    replys: [
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      },
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      }
    ],
    hidereply: false,
  },
  {
    id: 2,
    user: {
      name: "Nguyen Van D",
      img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
      level: 3
    },
    content: "Truyện hay",
    date: "2021-01-01",
    chaps: 4173,
    like: 100,

    replys: [
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      },
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      }
    ],
    hidereply: false,
  },
  {
    id: 2,
    user: {
      name: "Nguyen Van C",
      img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
      level: 4
    },
    content: "Truyện hay",
    date: "2021-01-01",
    chaps: 4173,
    like: 100,
    replys: [
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      },
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      }
    ],
    hidereply: false,
  },
  {
    id: 4,
    user: {
      name: "Nguyen Van B",
      img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
      level: 4
    },
    content: "Truyện hay",
    date: "2021-01-01",
    chaps: 4173,
    like: 100,
    replys: [
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      },
      {
        reply_id: 1,
        user: {
          name: "Nguyen Van A",
          img: "https://static.cdnno.com/user/b5a5e2e8958e765c2822d5cf7c60df7d/100.jpg?1592316927",
          level: 4
        },
        content: "Truyện hay",
        date: "2021-01-01 12:00:00",
        like: 100
      }
    ],
    hidereply: false,
  }
]
const notes = [
  {
    number: 1,
    content: "Không được dẫn link hoặc nhắc đến website khác"
  },
  {
    number: 2,
    content: "Không được có những từ ngữ gay gắt, đả kích, xúc phạm người khác"
  },
  {
    number: 3,
    content: "Đánh giá hoặc bình luận không liên quan tới truyện sẽ bị xóa"
  },
  {
    number: 4,
    content:
      "Đánh giá hoặc bình luận chê truyện một cách chung chung không mang lại giá trị cho người đọc sẽ bị xóa"
  }
]
</script>
