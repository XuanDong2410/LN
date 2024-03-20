<template>
  <q-page class="bg-light-50 max-w-1200px mx-auto cursor-pointer">
    <!-- <component :is="top" /> -->
    <component :is="weekly" :novels="weeklyNovel" class="my-5" />
    <div class="q-pa-md w-100% m-auto row">
      <div class="col-12">
        <div class="text-h6 text-bold opacity-70">Biên tập viên đề cử</div>
        <Component :is="list" :list-novel="modRanks" />
      </div>
      <!-- <div class="col-4">
        <div class="text-h6 text-bold opacity-70">Đang đọc</div>
        <q-list class="">
          <q-item v-for="item in CountNovel" class="m-0">
            <q-item-section thumbnail class="m-0.3 img-hover-zoom">
              <q-img
                :src="item.img"
                class="w-32px h-46px img-novel rounded-2px"
              />
            </q-item-section>
            <q-item-section class="m-0">
              <q-item-label
                lines="1"
                class="text-11px text-bold text-opacity-70 name-novel"
                >{{ item.name }}</q-item-label
              >
              <q-item-label caption>
                Đã đọc: {{ item.read_at }}/{{ item.chap
                }}<q-icon class="mb-0.7"><i-mdi-trash /></q-icon>
              </q-item-label>
            </q-item-section>
            <q-chip
              clickable
              class="text-11px text-center text-yellow-500 bg-white"
            >
              Đọc tiếp
            </q-chip>
          </q-item>
          <q-separator spaced inset />
        </q-list>

      </div> -->
    </div>
    <div class="m-2 text-20px text-bold">Thịnh hành</div>
    <component :is="updates" :novels="NovelUpdates" :slides-per-view="6" />
    <component :is="rank" />
    <div class="q-pa-md">
      <div class="text-h6 text-bold opacity-70">Hot Weekly</div>
    </div>
    <component :is="arrivals" :novels="weeklyNovel" />
    <component :is="vote" :votes="Votes" :feed-backs="FeedBacks" />
    <div class="q-pa-md">
      <div class="text-h6 text-bold opacity-70">You May Also Like</div>
    </div>
    <component :is="updates" :novels="NovelUpdates" :slides-per-view="6" />
  </q-page>
</template>

<script lang="ts" setup>
// Import Swiper Vue.js components
// import {
//   Autoplay,
//   // eslint-disable-next-line @typescript-eslint/no-unused-vars
//   EffectCreative,
//   Navigation,
//   Pagination
// } from "swiper/modules"
// import { Swiper, SwiperSlide } from "swiper/vue"

// Import Swiper styles

import arrivals from "../components/home/arrivals.vue"
import list from "../components/home/list.vue"
import rank from "../components/home/rank.vue"
import vote from "../components/home/vote.vue"
// import top from "../components/home/top.vue"
import weekly from "../components/home/weekly.vue"
import updates from "../components/updates.vue"
import reads from "../data/home/read.json"
import weeklyNovel from "../data/home/weekly.json"
import NovelUpdates from "../data/updates.json"
import FeedBacks from "../data/user/feedback.json"
// import ListNovel from "../data/user/listNovel.json"
import Votes from "../data/user/vote.json"

const CountNovel = computed(() => {
  return reads.slice(0, 6)
})
// const slide = ref(1)
// import required modules
const modRanks = [
  {
    value: 1,
    img: "https://static.cdnno.com/poster/theo-tram-yeu-tru-ma-bat-dau-truong-sinh-bat-tu/150.jpg?1702546489",
    name: "Theo Trảm Yêu Trừ Ma Bắt Đầu Trường Sinh Bất Tử",
    author: "Lục Nguyệt Thập Cửu",
    describe:
      "Tiêu hao thọ nguyên quán chú võ học, có thể không hạn tiến hành thôi diễn. Thẩm Nghi phàm nhân thân thể, số tuổi thọ không hơn trăm năm, may mà có khả năng thông qua chém giết yêu ma thu hoạch đối phương còn thừa thọ nguyên. Tại Tà Túy khắp nơi trên đất trong loạn thế lộ ra trường đao, nhường đám này sống trăm ngàn năm sinh linh sợ vỡ mật! Theo .",
    genre: "Huyền Huyễn",
    points: 1000
  },
  {
    value: 2,
    img: "https://static.cdnno.com/poster/xich-tam-tuan-thien/150.jpg?1612524612",
    name: "Xích Tâm Tuần Thiên",
    author: "Tình Hà Dĩ Thậm",
    describe:
      "Thời đại thượng cổ, Yêu tộc tuyệt tích. Thời đại cận cổ, Long tộc biến mất. Thần đạo đang thịnh thời đại đã như khói, phi kiếm đỉnh cao nhất thời đại cuối cùng trầm luân. . .",
    genre: "Tiên Hiệp",
    points: 1000
  },
  {
    value: 3,
    img: "https://static.cdnno.com/poster/quoc-vuong-1/150.jpg?1663492433",
    name: "Quốc Vương",
    author: "Tân Hải Nguyệt 1",
    describe:
      "Vạn tộc cùng tồn tại, kiếm cùng ma pháp hoà lẫn, Nhân tộc, Hải tộc, Tinh Linh, Ải Nhân, Thú Nhân... Giành trước nở rộ văn minh chi quang, viết lên sử thi bi ca!",
    genre: "Kỳ Ảo",
    points: 1000
  },
  {
    value: 4,
    img: "https://static.cdnno.com/poster/tu-la-trang-nguoi-choi/150.jpg?1709361855",
    name: "Tu La Tràng Người Chơi",
    author: "Thì Cửu Mệnh",
    describe:
      "“Ta hôm nay đột nhiên phát hiện thế giới này rất nguy hiểm.” Bạch Chỉ một mặt nghiêm túc tại trên máy tính gõ ra một hàng chữ. “Hôm nay lúc đi ra ngoài, ta phát hiện ven đường có người ở cắn người, vài tên dám làm việc nghĩa tiểu tử vọt ra đem tội",
    genre: "Kỳ Ảo",
    points: 1000
  },
  {
    value: 5,
    img: "https://static.cdnno.com/poster/ta-mot-nguoi-nem-lan-tan-the/150.jpg?1651288364",
    name: "Ta Một Người Ném Lăn Tận Thế",
    author: "Tân Phong",
    describe:
      "Một người ném lăn tận thế nhân sinh chi lộ. Tang thi: Rống. Sở Trần: 'Tất cả mọi người là hàng xóm, tại sao phải táo bạo như vậy đây.' Sở Trần: 'Ta còn muốn đi mua món ăn đây. Sở Trần nhìn xem biến thành tang thi Tiểu Thanh: 'Tiểu Thanh, ta mua..",
    genre: "Huyền Huyễn",
    points: 1000
  },
  {
    value: 6,
    img: "https://static.cdnno.com/poster/quang-am-chi-ngoai/150.jpg?1655013821",
    name: "Quang Âm Chi Ngoại",
    author: "Nhĩ Căn",
    describe:
      "Thiên địa là vạn vật chúng sinh khách xá, quang âm là từ xưa tới nay khách qua đường. Tử sinh khác biệt, thật giống như mộng cùng tỉnh khác biệt, xôn xao biến hóa, không thể cật vấn. Như vậy siêu việt sinh tử, đã vượt ra thiên địa, tại quang âm bên",
    genre: "Huyền Huyễn",
    points: 1000
  },
  {
    value: 7,
    img: "https://static.cdnno.com/poster/kinh-khung-tu-tien-lo/150.jpg?1688145713",
    name: "Kinh Khủng Tu Tiên Lộ",
    author: "Đầu Ngận Đại Đích T Quân",
    describe:
      "(quỷ dị + tàn khốc tu tiên + lão Lục + phía sau màn, « vô đạo tiên lộ » « thần bí, tiên lộ, câu cá",
    genre: "Huyền Huyễn",
    points: 1000
  },
  {
    value: 8,
    img: "https://static.cdnno.com/poster/tan-the-ta-tu-mau-chot-so-nguoi-khac-them-mot-cai/150.jpg?1680454384",
    name: "Tận Thế: Ta Từ Mấu Chốt So Người Khác Thêm Một Cái",
    author: "Miên Y Vệ",
    describe:
      "Dũng cảm, hèn mọn, thiện lương, gian xảo, khoan hậu, tham lam, ưu nhã, hung ác, vui vẻ, biến thái, chính trực, giả vờ chính đáng...",
    genre: "Khoa Huyễn",
    points: 1000
  },
  {
    value: 9,
    img: "https://static.cdnno.com/poster/chay-mau-ma-dau-kia-lai-toi/150.jpg?1687347306",
    name: "Chạy Mau! Ma Đầu Kia Tới",
    author: "Hiêu Trương Bá Khí Đích Văn Tử",
    describe:
      "Từ Lạc là một vị Ma Đạo tu sĩ, hắn có một khối Giới Bia, có thể xuyên qua đến những giới vực khá",
    genre: "Huyền Huyễn",
    points: 1000
  }
]
// import required modules
</script>
<style>
.img-hover-zoom {
  overflow: hidden; /* Đảm bảo rằng không có phần nào của hình ảnh bị lộ ra ngoài khung chứa */
}

.img-hover-zoom img {
  transition: transform 0.5s ease; /* Đặt thời gian chuyển đổi và hiệu ứng */
}

.img-hover-zoom:hover img {
  transform: scale(1.2); /* Phóng to hình ảnh khi hover */
}
/*
.swiper {
  width: 100%;
  padding-top: 50px;
  padding-bottom: 50px;
}
*/

/*
.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
}


// .swiper {
//   margin: auto;
//   width: 80%;
//   height: 450px;
// }
*/
</style>
