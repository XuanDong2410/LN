<template>
  <div class="row m-auto d-flex justify-center">
    <q-card
      bordered
      padding
      v-for="rank in ranks"
      class="rounded-borders col-3 m-3"
    >
      <q-item-label class="text-bold text-18px" header>
        {{ rank.name }}
      </q-item-label>
      <q-item v-for="item in rank.items" clickable v-ripple>
        <q-icon v-if="item.value === 1" class="size-2.5em mt-2">
          <i-emojione-1st-place-medal />
        </q-icon>
        <q-icon v-if="item.value === 2" class="size-2em">
          <i-emojione-2nd-place-medal class="size-4m" />
        </q-icon>
        <q-icon v-if="item.value === 3" class="size-2em">
          <i-emojione-3rd-place-medal class="size-4m" />
        </q-icon>

        <q-icon v-if="item.value > 3" class="size-2em text-center mr-1">
          {{ item.value }}.
        </q-icon>
        <q-item-section v-if="item.value === 1">
          <q-item-label
            lines="1"
            class="text-bold opacity-75 text-13px name-novel"
          >
            {{ item.name }}
          </q-item-label>

          <q-item-label lines="1" caption class="text-yellow-400 text-15px">
            {{ item.points }}
            <q-icon v-if="rank.index === 1" class="size-1.5em mb-1"
              ><i-mdi-eye
            /></q-icon>
            <q-icon v-if="rank.index === 2" class="size-1.5em mb-1"
              ><i-mdi-arrow-top-bold-circle
            /></q-icon>
            <q-icon v-if="rank.index === 3" class="size-1.5em mb-1"
              ><i-uil-flower
            /></q-icon>
          </q-item-label>
          <q-item-label lines="1" caption>
            <q-icon><i-mingcute-user-edit-fill /></q-icon>
            {{ item.author }}
          </q-item-label>
          <q-item-label lines="1" caption>
            <q-icon><i-fa-book /></q-icon>
            {{ item.genre }}
          </q-item-label>
        </q-item-section>
        <q-item-section v-if="item.value != 1">
          <q-item-label lines="1" class="opacity-85 name-novel">
            {{ item.name }}
          </q-item-label>
          <q-separator class="mt-1" />
        </q-item-section>
        <q-item-section v-if="item.value === 1" thumbnail>
          <div class="book-cover">
            <img :src="item.img" />
            <span class="book-cover-shadow"></span>
          </div>
        </q-item-section>

        <q-item-section v-if="item.value == 1" side> </q-item-section>
        <q-item-section v-if="item.value != 1" side>
          {{ item.points }}
        </q-item-section>
      </q-item>
    </q-card>
  </div>
</template>
<script lang="ts" setup>
const ranks = [
  {
    index: 1,
    name: "Đọc nhiều tuần",
    items: [
      {
        value: 1,
        img: "https://static.cdnno.com/poster/su-huynh-cua-ta-qua-manh/150.jpg?1656784900",
        name: "Xích Tâm Tuần Thiên",
        author: "Nhâm Ngã Tiếu",
        genre: "Huyền Huyễn",
        points: 1000
      },
      {
        value: 2,
        img: "",
        name: "Vạn Cổ Thần Đế",
        author: "Phi Thiên Ngư",
        genre: "Huyền Huyễn",
        points: 9001
      },
      {
        value: 3,
        img: "",
        name: "Đế Bá",
        genre: "Kỳ Ảo",
        points: 800
      },
      {
        value: 4,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 5,
        name: "Xích Tâm Tuần Thiên",
        points: 700
      },
      {
        value: 6,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 7,
        name: "Xích Tâm Tuần Thiên",
        points: 700
      },
      {
        value: 8,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 9,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 10,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      }
    ]
  },
  {
    index: 2,
    name: "Thịnh hành tuần",
    items: [
      {
        value: 1,
        img: "https://static.cdnno.com/poster/vo-dao-truong-sinh-gia-thiet-muc-tieu-lien-co-the-hoan-thanh/150.jpg?1695971479",
        name: "Xích Tâm Tuần Thiên",
        author: "Nhâm Ngã Tiếu",
        genre: "Huyền Huyễn",
        points: 1000
      },
      {
        value: 2,
        img: "",
        name: "Vạn Cổ Thần Đế",
        author: "Phi Thiên Ngư",
        genre: "Huyền Huyễn",
        points: 900
      },
      {
        value: 3,
        img: "",
        name: "Đế Bá",
        genre: "Kỳ Ảo",
        points: 800
      },
      {
        value: 4,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 5,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 6,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 7,
        name: "Xích Tâm Tuần Thiên",
        points: 700
      },
      {
        value: 8,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 9,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 10,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      }
    ]
  },
  {
    index: 3,
    name: "Đề cử tuần",
    items: [
      {
        value: 1,
        img: "https://static.cdnno.com/poster/su-huynh-cua-ta-qua-manh/150.jpg?1656784900",
        name: "Xích Tâm Tuần Thiên",
        author: "Nhâm Ngã Tiếu",
        genre: "Huyền Huyễn",
        points: 1000
      },
      {
        value: 2,
        img: "",
        name: "Vạn Cổ Thần Đế",
        author: "Phi Thiên Ngư",
        genre: "Huyền Huyễn",
        points: 900
      },
      {
        value: 3,
        img: "",
        name: "Đế Bá",
        genre: "Kỳ Ảo",
        points: 800
      },
      {
        value: 4,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 5,
        name: "Xích Tâm Tuần Thiên",
        points: 700
      },
      {
        value: 6,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 7,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 8,
        name: "Xích Tâm Tuần Thiên",
        points: 600
      },
      {
        value: 9,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      },
      {
        value: 10,
        name: "Xích Tâm Tuần Thiên",
        points: 500
      }
    ]
  }
]
</script>
<style>
.name-novel:hover {
  color: rgb(218, 110, 27);
  cursor: pointer;
}
.book-cover {
  -webkit-text-size-adjust: 100%;
  -webkit-tap-highlight-color: transparent;
  font-family:
    Source Sans Pro,
    -apple-system,
    BlinkMacSystemFont,
    Segoe UI,
    Roboto,
    Helvetica Neue,
    Arial,
    sans-serif;
  font-size: 0.9375rem;
  font-weight: 400;
  line-height: 1.5;
  color: #333;
  list-style: none;
  box-sizing: border-box;
  transform: perspective(70px) rotateY(-10deg);
  box-shadow: 0 0 5 2 black;
}
.book-cover img {
  -webkit-text-size-adjust: 100%;
  -webkit-tap-highlight-color: transparent;
  font-family:
    Source Sans Pro,
    -apple-system,
    BlinkMacSystemFont,
    Segoe UI,
    Roboto,
    Helvetica Neue,
    Arial,
    sans-serif;
  font-size: 0.9375rem;
  font-weight: 400;
  line-height: 1.5;
  list-style: none;
  color: #333;
  box-sizing: border-box;
  border-style: solid;
  vertical-align: middle;
  width: 70px;
  height: 105px;
  outline: 1px solid transparent;
}
.book-cover-link {
  -webkit-text-size-adjust: 100%;
  -webkit-tap-highlight-color: transparent;
  font-family:
    Source Sans Pro,
    -apple-system,
    BlinkMacSystemFont,
    Segoe UI,
    Roboto,
    Helvetica Neue,
    Arial,
    sans-serif;
  font-size: 0.9375rem;
  font-weight: 400;
  line-height: 1.5;
  list-style: none;
  box-sizing: border-box;
  color: #333;
  background-color: transparent;
  text-decoration: none;
  position: relative;
  z-index: 10;
  display: inline-block;
  transform: translateZ(50px);
  transition: all 0.2s ease-in-out;
}
.book-cover::after {
  position: absolute;
  z-index: 2;
  top: 2%;
  left: 99%;
  width: 10%;
  height: 96%;
  content: " ";
  -webkit-transform: perspective(70px) rotateY(30deg);
  -moz-transform: perspective(70px) rotateY(30deg);
  transform: perspective(70px) rotateY(30deg);
  background-color: #efefef;
  -webkit-box-shadow: inset 0 0 5px #333;
  -moz-box-shadow: inset 0 0 5px #333;
  box-shadow: inset 0 0 5px #333;
}
</style>
