import { report } from 'process'; import { report } from 'process'; import {
report } from 'process';
<template>
  <q-list>
    <q-item>
      <q-item-label class="text-bold mt-1 text-16px"
        >Liên hệ Hỗ trợ</q-item-label
      >
    </q-item>
    <q-separator />
    <q-item class="mb-4 text-justify text-13px">
      <q-item-label class="text-body line-height-18px">
        Trước khi yêu cầu hỗ trợ vui lòng đọc kỹ
        <span>
          <q-chip class="bg-white text-yellow-600 m-0" clickable
            >Những câu hỏi thường gặp</q-chip
          ></span
        >, nếu vấn đề bạn cần hỗ trợ không có trong những câu hỏi thường gặp
        hãy<span>
          <q-chip class="text-14px bg-white text-yellow-600 m-0" clickable
            >để lại lời nhắn</q-chip
          ></span
        >, chúng tôi sẽ trả lời bạn qua email khi làm việc trở lại, giờ làm việc
        từ 8h - 20h (GMT+07)
      </q-item-label>
    </q-item>
    <q-item class="mb-4 text-13px">
      <q-item-label>
        <div>
          <p class="text-body">
            <b>-Lưu ý:</b>
            <span>
              Vui lòng không hỏi cách làm nhiệm vụ nhận thưởng, hỗ trợ viên sẽ
              không trả lời bất cứ câu hỏi nào về vấn đề làm nhiệm vụ nhận
              thưởng
            </span>
          </p>
        </div>
      </q-item-label>
    </q-item>
    <q-separator />
    <q-item>
      <q-item-label class="text-bold mt-1 text-16px">
        Danh sách trợ giúp & báo lỗi
      </q-item-label>
    </q-item>
    <q-separator />
    <q-item v-for="report in reports">
      <q-item-section>
        <q-item-label class="text-green-500">
          Báo lỗi: {{ report.name }}
        </q-item-label>
        <q-item-label caption>
          Nội dung người lớn: {{ report.age ? "Yes" : "No Content" }}
        </q-item-label>
        <q-separator />
      </q-item-section>
      <q-item-section class="text-red-800" top side>
        <q-item-label>
          {{ report.status ? "Đã xử lý" : "Đang xử lý" }}
        </q-item-label>
      </q-item-section>
    </q-item>
  </q-list>
</template>
<script lang="ts" setup>
const reports = [
  {
    index: 1,
    name: "Chương 1505: Cửu U xưng Vương",
    age: false,
    status: true,
    date: "2022-05-15"
  },
  {
    index: 2,
    name: "Chương 1505: Cửu U xưng Vương",
    age: true,
    status: true,
    date: "2022-05-15"
  },
  {
    index: 3,
    name: "Chương 1505: Cửu U xưng Vương",
    age: false,
    status: false,
    date: "2022-05-15"
  },
  {
    index: 4,
    name: "Chương 1505: Cửu U xưng Vương",
    age: true,
    status: false,
    date: "2022-05-15"
  },
  {
    index: 5,
    name: "Chương 1505: Cửu U xưng Vương",
    age: true,
    status: false,
    date: "2022-05-15"
  },
  {
    index: 6,
    name: "Chương 1505: Cửu U xưng Vương",
    age: true,
    status: false,
    date: "2022-05-15"
  },
  {
    index: 7,
    name: "Chương 1505: Cửu U xưng Vương",
    age: true,
    status: false,
    date: "2022-05-15"
  }
]
</script>
