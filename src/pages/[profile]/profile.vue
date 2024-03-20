<route lang="yaml">
name: "profile"
</route>
<template>
  <q-page class="row m-2 my-5">
    <q-card class="offset-1 col-7" flat>
      <swiper
        :css-mode="true"
        :navigation="true"
        :pagination="true"
        :mousewheel="true"
        :keyboard="true"
        :loop="true"
        :speed="1000"
        :auto-play="2500"
        :modules="[Navigation, Pagination, Mousewheel, Keyboard]"
        class="mySwiper"
      >
        <swiper-slide
          v-for="(novel, index) in data"
          :key="index"
          class="bg-gray-400 h-100%"
        >
          <q-item class="w-80% m-auto p-5">
            <q-item-section class="col-3">
              <img :src="novel.img" class="w-120px box-shadow img-novel" />
            </q-item-section>
            <q-item-section class="col-8">
              <q-item-label
                lines="1"
                class="mb-2 text-bold text-15px opacity-90 name-novel"
              >
                {{ novel.name }}
              </q-item-label>
              <q-chip class="bg-white text-caption opacity-70 text-11px mt-2">
                <i-prime-user-edit size="1.5em" /> {{ novel.author }}
                <q-space /> <i-ph-book-bold size="1em" /> {{ novel.genre }}
              </q-chip>
              <q-item-label
                class="opacity-70 text-caption text-justify my-2"
                lines="4"
              >
                {{ novel.describe }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </swiper-slide>
      </swiper>
      <div class="text-h6 m-2 opacity-80 text-bold">Posted</div>
      <q-list v-for="(novel, index) in data" :key="index">
        <q-item class="h-100%">
          <q-item-section class="col-2">
            <img :src="novel.img" class="w-90px box-shadow img-novel" />
          </q-item-section>
          <q-item-section class="col-10">
            <q-item-label
              lines="1"
              class="mb-2 text-bold text-13px opacity-90 name-novel"
            >
              {{ novel.name }}
            </q-item-label>
            <q-item-label
              class="opacity-70 text-caption text-justify my-2"
              lines="3"
            >
              {{ novel.describe }}
            </q-item-label>
            <q-chip class="bg-white text-caption opacity-70 text-11px mt-2">
              <i-prime-user-edit size="1.5em" /> {{ novel.author }} <q-space />
              <i-ph-book-bold size="1em" /> {{ novel.genre }} <q-space />
              <i-raphael-page size="1em" />{{ novel.chap }} chaps <q-space />
              <i-fluent-glasses-20-regular size="1em" />{{ novel.read }}
            </q-chip>
          </q-item-section>
        </q-item>
        <q-separator />
      </q-list>
      <q-pagination
        v-model="current"
        :max="max"
        direction-links
        color="orange"
        active-design="unelevated"
        active-color="brown"
        active-text-color="orange"
        class="d-flex justify-center my-5"
        align="center"
      />
    </q-card>

    <q-card class="col-3" flat>
      <q-list class="max-w-170">
        <q-item>
          <q-avatar class="size-1.5em">
            <q-img
              src="https://static.cdnno.com/user/7b6ca64c0381d9743781acfc797c8ba6/100.jpg?1642616770"
            />
          </q-avatar>
          <q-item-section class="ml-2">
            <q-item-label class="text-bold text-opacity-80 text-16px">
              {{ profile }}
              <q-chip class="text-orange-500 b-solid text-13px" outline spare>{{
                currentLevel?.name
              }}</q-chip>
            </q-item-label>
            <q-item-label text-caption>3 năm trước</q-item-label>
          </q-item-section>
        </q-item>
        <q-item>
          <q-item-section class="m-auto">
            {{ description }}
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
            Lv.{{ currentLevel?.index }}
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
            <q-item-label>Publish</q-item-label>
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
      </q-list>
    </q-card>
  </q-page>
</template>

<script lang="ts" setup>
// Import Swiper styles
import "swiper/css"

import "swiper/css/navigation"
import "swiper/css/pagination"

// import required modules
import { Keyboard, Mousewheel, Navigation, Pagination } from "swiper/modules"
import { Swiper, SwiperSlide } from "swiper/vue"

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
/// List Novels
const ListNovels = [
  {
    index: 1,
    name: "Tử Linh Pháp Sư Tại Tận Thế Điên Cuồng Đóng Quân",
    author: "Phẫn Nộ Đích Thực Nhân Ngư",
    genre: "Kỳ Ảo",
    read: 1999,
    chap: 70,
    img: "https://static.cdnno.com/poster/tu-linh-phap-su-tai-tan-the-dien-cuong-dong-quan/150.jpg?1709409622",
    describe:
      "【 hư giả tử linh pháp sư, binh nguyên không đủ, bị người bài xích truy sát.】【 chân thực tử linh pháp sư, vô số khô lâu, thành tựu chúa tể một phương. 】Vũ Hành khi lấy được song xuyên cửa về sau, phát hiện nguyên bản thế giới trải rộng Zombie.Làm một tên nhà buôn kế hoạch thất bại, bắt đầu một cái khác sống tiếp kế hoạch.Vũ Hành lựa chọn trở thành một tên 'Tử linh pháp sư' .Dị giới không cho phép triệu hoán vong linh? Tận thế toàn bộ tinh cầu đều là binh nguyên.Zombie thế giới không cách nào sinh tồn? Vậy ta tại dị giới sinh hoạt học tập kỹ năng.Từ đây thế giới xuất hiện một con trang bị vũ khí hiện đại vong linh đại quân.Thiên tai tiếp cận, trăm vạn khô lâu.Bất tử cốt long, vong linh quân vương.(song xuyên cửa + tử linh pháp sư + ma pháp + kỳ huyễn thế giới + vong linh thiên tai. )"
  },
  {
    index: 2,
    name: "Ai Bảo Ngươi Năng Lực Như Thế Dùng?",
    author: "Thái Bạch Thủy Quân",
    genre: "Huyền Huyễn",
    read: 156653,
    chap: 550,
    img: "https://static.cdnno.com/poster/ai-bao-nguoi-nang-luc-nhu-the-dung/150.jpg?1691777892",
    describe:
      "Toàn dân thức tỉnh thế giới bên trong, chư giới hội tụ thành bí cảnh, các Giác Tỉnh giả cho rằng bọn họ là Chư Thiên Vạn Giới trung tâm, thẳng đến bí cảnh xâm lấn, vương triều những năm cuối, thế giới đổ sụp các loại sự kiện lớn cho bọn hắn một cái vang dội bạt tai mạnh.. . .Ta phải tìm tới là ai đem ta một ngàn vạn biến thành một ngàn! Vương Lâm Trì bị ép phấn đấu sau nói như vậy."
  },
  {
    index: 3,
    name: "Lần Này Không Làm Nhà Huấn Luyện",
    author: "Kỵ Xa Đích Phong",
    genre: "Đồng Nhân",
    read: 70427,
    chap: 369,
    img: "https://static.cdnno.com/poster/lan-nay-khong-lam-nha-huan-luyen/150.jpg?1704308389",
    describe:
      "Naoki xuyên qua đến Pokémon thế giới kế thừa một nhà nông trường, cũng thu được dùng món ăn cho Pokémon mang đến thần kỳ lực lượng năng lực.Nông trường bên trong Pokémon trên thân bởi vậy sinh ra một chút biến hóa kỳ diệu.Có thể ba trăm sáu mươi độ không góc chết không sau dao sử dụng ra [ siêu cấp Rollout [ Lăn ] ] Miltank, tốc độ như Tật Phong Tấn Lôi những nơi đi qua đều là tàn ảnh Cyclizar, có thể một cái búa đánh bay Snorlax song đuôi ngựa siêu cấp đại lực sĩ Tinkaton. . ."
  },
  {
    index: 4,
    name: "Tận Thế: Ta Từ Mấu Chốt So Người Khác Thêm Một Cái",
    author: "Miên Y Vệ",
    genre: "Khoa Huyễn",
    read: 555550,
    chap: 624,
    img: "https://static.cdnno.com/poster/tan-the-ta-tu-mau-chot-so-nguoi-khac-them-mot-cai/150.jpg?1680454384",
    describe:
      "Dũng cảm, hèn mọn, thiện lương, gian xảo, khoan hậu, tham lam, ưu nhã, hung ác, vui vẻ, biến thái, chính trực, giả vờ chính đáng...Tại cái này tận thế đồng dạng thế giới, chỉ có tại dị tinh chiến trường thủ thắng mới có thể thu được lấy tư nguyên, cam đoan văn minh kéo dài.Mỗi cái tiến vào dị tinh chiến trường chiến sĩ, đều sẽ ngẫu nhiên thu hoạch được một cái thuộc về mình từ mấu chốt.Nói chuyện hành động phù hợp từ mấu chốt, các hạng thuộc tính liền sẽ phi tốc trưởng thành, thu hoạch được siêu nhân năng lực giống nhau, trái lại, người thiết lập sụp đổ, liền sẽ cấp tốc suy yếu;Đây là một cái liều diễn kỹ thế giới;"
  },
  {
    index: 5,
    name: "Tam Quốc: Ai Bảo Hắn Làm Mưu Sĩ?",
    author: "Tam Thiên Tứ Bao",
    genre: "Dã Sử",
    read: 27938,
    chap: 250,
    img: "https://static.cdnno.com/poster/tam-quoc-ai-bao-han-lam-muu-si/150.jpg?17014238584",
    describe:
      "Trương Hàn xuyên qua Hán mạt Tam quốc, không chỗ có thể đi lúc, dấn thân vào Tào doanh. Thức tỉnh 【 công thành hệ thống 】, chỉ cần lập công liền có thể đạt được ban thưởng, thế là Trương Hàn khổ luyện võ nghệ, anh dũng chém giết, rốt cục thông qua không ngừng lập công đem 【 vũ lực 】 tăng lên trên diện rộng về sau, ngang nhiên chuyển thành tâm tâm niệm niệm mưu thần!"
  },
  {
    index: 2,
    name: "Ai Bảo Ngươi Năng Lực Như Thế Dùng?",
    author: "Thái Bạch Thủy Quân",
    genre: "Huyền Huyễn",
    read: 156653,
    chap: 550,
    img: "https://static.cdnno.com/poster/ai-bao-nguoi-nang-luc-nhu-the-dung/150.jpg?1691777892",
    describe:
      "Toàn dân thức tỉnh thế giới bên trong, chư giới hội tụ thành bí cảnh, các Giác Tỉnh giả cho rằng bọn họ là Chư Thiên Vạn Giới trung tâm, thẳng đến bí cảnh xâm lấn, vương triều những năm cuối, thế giới đổ sụp các loại sự kiện lớn cho bọn hắn một cái vang dội bạt tai mạnh.. . .Ta phải tìm tới là ai đem ta một ngàn vạn biến thành một ngàn! Vương Lâm Trì bị ép phấn đấu sau nói như vậy."
  },
  {
    index: 3,
    name: "Lần Này Không Làm Nhà Huấn Luyện",
    author: "Kỵ Xa Đích Phong",
    genre: "Đồng Nhân",
    read: 70427,
    chap: 369,
    img: "https://static.cdnno.com/poster/lan-nay-khong-lam-nha-huan-luyen/150.jpg?1704308389",
    describe:
      "Naoki xuyên qua đến Pokémon thế giới kế thừa một nhà nông trường, cũng thu được dùng món ăn cho Pokémon mang đến thần kỳ lực lượng năng lực.Nông trường bên trong Pokémon trên thân bởi vậy sinh ra một chút biến hóa kỳ diệu.Có thể ba trăm sáu mươi độ không góc chết không sau dao sử dụng ra [ siêu cấp Rollout [ Lăn ] ] Miltank, tốc độ như Tật Phong Tấn Lôi những nơi đi qua đều là tàn ảnh Cyclizar, có thể một cái búa đánh bay Snorlax song đuôi ngựa siêu cấp đại lực sĩ Tinkaton. . ."
  },
  {
    index: 4,
    name: "Tận Thế: Ta Từ Mấu Chốt So Người Khác Thêm Một Cái",
    author: "Miên Y Vệ",
    genre: "Khoa Huyễn",
    read: 555550,
    chap: 624,
    img: "https://static.cdnno.com/poster/tan-the-ta-tu-mau-chot-so-nguoi-khac-them-mot-cai/150.jpg?1680454384",
    describe:
      "Dũng cảm, hèn mọn, thiện lương, gian xảo, khoan hậu, tham lam, ưu nhã, hung ác, vui vẻ, biến thái, chính trực, giả vờ chính đáng...Tại cái này tận thế đồng dạng thế giới, chỉ có tại dị tinh chiến trường thủ thắng mới có thể thu được lấy tư nguyên, cam đoan văn minh kéo dài.Mỗi cái tiến vào dị tinh chiến trường chiến sĩ, đều sẽ ngẫu nhiên thu hoạch được một cái thuộc về mình từ mấu chốt.Nói chuyện hành động phù hợp từ mấu chốt, các hạng thuộc tính liền sẽ phi tốc trưởng thành, thu hoạch được siêu nhân năng lực giống nhau, trái lại, người thiết lập sụp đổ, liền sẽ cấp tốc suy yếu;Đây là một cái liều diễn kỹ thế giới;"
  },
  {
    index: 5,
    name: "Tam Quốc: Ai Bảo Hắn Làm Mưu Sĩ?",
    author: "Tam Thiên Tứ Bao",
    genre: "Dã Sử",
    read: 27938,
    chap: 250,
    img: "https://static.cdnno.com/poster/tam-quoc-ai-bao-han-lam-muu-si/150.jpg?17014238584",
    describe:
      "Trương Hàn xuyên qua Hán mạt Tam quốc, không chỗ có thể đi lúc, dấn thân vào Tào doanh. Thức tỉnh 【 công thành hệ thống 】, chỉ cần lập công liền có thể đạt được ban thưởng, thế là Trương Hàn khổ luyện võ nghệ, anh dũng chém giết, rốt cục thông qua không ngừng lập công đem 【 vũ lực 】 tăng lên trên diện rộng về sau, ngang nhiên chuyển thành tâm tâm niệm niệm mưu thần!"
  },
  {
    index: 2,
    name: "Ai Bảo Ngươi Năng Lực Như Thế Dùng?",
    author: "Thái Bạch Thủy Quân",
    genre: "Huyền Huyễn",
    read: 156653,
    chap: 550,
    img: "https://static.cdnno.com/poster/ai-bao-nguoi-nang-luc-nhu-the-dung/150.jpg?1691777892",
    describe:
      "Toàn dân thức tỉnh thế giới bên trong, chư giới hội tụ thành bí cảnh, các Giác Tỉnh giả cho rằng bọn họ là Chư Thiên Vạn Giới trung tâm, thẳng đến bí cảnh xâm lấn, vương triều những năm cuối, thế giới đổ sụp các loại sự kiện lớn cho bọn hắn một cái vang dội bạt tai mạnh.. . .Ta phải tìm tới là ai đem ta một ngàn vạn biến thành một ngàn! Vương Lâm Trì bị ép phấn đấu sau nói như vậy."
  },
  {
    index: 3,
    name: "Lần Này Không Làm Nhà Huấn Luyện",
    author: "Kỵ Xa Đích Phong",
    genre: "Đồng Nhân",
    read: 70427,
    chap: 369,
    img: "https://static.cdnno.com/poster/lan-nay-khong-lam-nha-huan-luyen/150.jpg?1704308389",
    describe:
      "Naoki xuyên qua đến Pokémon thế giới kế thừa một nhà nông trường, cũng thu được dùng món ăn cho Pokémon mang đến thần kỳ lực lượng năng lực.Nông trường bên trong Pokémon trên thân bởi vậy sinh ra một chút biến hóa kỳ diệu.Có thể ba trăm sáu mươi độ không góc chết không sau dao sử dụng ra [ siêu cấp Rollout [ Lăn ] ] Miltank, tốc độ như Tật Phong Tấn Lôi những nơi đi qua đều là tàn ảnh Cyclizar, có thể một cái búa đánh bay Snorlax song đuôi ngựa siêu cấp đại lực sĩ Tinkaton. . ."
  },
  {
    index: 4,
    name: "Tận Thế: Ta Từ Mấu Chốt So Người Khác Thêm Một Cái",
    author: "Miên Y Vệ",
    genre: "Khoa Huyễn",
    read: 555550,
    chap: 624,
    img: "https://static.cdnno.com/poster/tan-the-ta-tu-mau-chot-so-nguoi-khac-them-mot-cai/150.jpg?1680454384",
    describe:
      "Dũng cảm, hèn mọn, thiện lương, gian xảo, khoan hậu, tham lam, ưu nhã, hung ác, vui vẻ, biến thái, chính trực, giả vờ chính đáng...Tại cái này tận thế đồng dạng thế giới, chỉ có tại dị tinh chiến trường thủ thắng mới có thể thu được lấy tư nguyên, cam đoan văn minh kéo dài.Mỗi cái tiến vào dị tinh chiến trường chiến sĩ, đều sẽ ngẫu nhiên thu hoạch được một cái thuộc về mình từ mấu chốt.Nói chuyện hành động phù hợp từ mấu chốt, các hạng thuộc tính liền sẽ phi tốc trưởng thành, thu hoạch được siêu nhân năng lực giống nhau, trái lại, người thiết lập sụp đổ, liền sẽ cấp tốc suy yếu;Đây là một cái liều diễn kỹ thế giới;"
  },
  {
    index: 5,
    name: "Tam Quốc: Ai Bảo Hắn Làm Mưu Sĩ?",
    author: "Tam Thiên Tứ Bao",
    genre: "Dã Sử",
    read: 27938,
    chap: 250,
    img: "https://static.cdnno.com/poster/tam-quoc-ai-bao-han-lam-muu-si/150.jpg?17014238584",
    describe:
      "Trương Hàn xuyên qua Hán mạt Tam quốc, không chỗ có thể đi lúc, dấn thân vào Tào doanh. Thức tỉnh 【 công thành hệ thống 】, chỉ cần lập công liền có thể đạt được ban thưởng, thế là Trương Hàn khổ luyện võ nghệ, anh dũng chém giết, rốt cục thông qua không ngừng lập công đem 【 vũ lực 】 tăng lên trên diện rộng về sau, ngang nhiên chuyển thành tâm tâm niệm niệm mưu thần!"
  },
  {
    index: 2,
    name: "Ai Bảo Ngươi Năng Lực Như Thế Dùng?",
    author: "Thái Bạch Thủy Quân",
    genre: "Huyền Huyễn",
    read: 156653,
    chap: 550,
    img: "https://static.cdnno.com/poster/ai-bao-nguoi-nang-luc-nhu-the-dung/150.jpg?1691777892",
    describe:
      "Toàn dân thức tỉnh thế giới bên trong, chư giới hội tụ thành bí cảnh, các Giác Tỉnh giả cho rằng bọn họ là Chư Thiên Vạn Giới trung tâm, thẳng đến bí cảnh xâm lấn, vương triều những năm cuối, thế giới đổ sụp các loại sự kiện lớn cho bọn hắn một cái vang dội bạt tai mạnh.. . .Ta phải tìm tới là ai đem ta một ngàn vạn biến thành một ngàn! Vương Lâm Trì bị ép phấn đấu sau nói như vậy."
  },
  {
    index: 3,
    name: "Lần Này Không Làm Nhà Huấn Luyện",
    author: "Kỵ Xa Đích Phong",
    genre: "Đồng Nhân",
    read: 70427,
    chap: 369,
    img: "https://static.cdnno.com/poster/lan-nay-khong-lam-nha-huan-luyen/150.jpg?1704308389",
    describe:
      "Naoki xuyên qua đến Pokémon thế giới kế thừa một nhà nông trường, cũng thu được dùng món ăn cho Pokémon mang đến thần kỳ lực lượng năng lực.Nông trường bên trong Pokémon trên thân bởi vậy sinh ra một chút biến hóa kỳ diệu.Có thể ba trăm sáu mươi độ không góc chết không sau dao sử dụng ra [ siêu cấp Rollout [ Lăn ] ] Miltank, tốc độ như Tật Phong Tấn Lôi những nơi đi qua đều là tàn ảnh Cyclizar, có thể một cái búa đánh bay Snorlax song đuôi ngựa siêu cấp đại lực sĩ Tinkaton. . ."
  },
  {
    index: 4,
    name: "Tận Thế: Ta Từ Mấu Chốt So Người Khác Thêm Một Cái",
    author: "Miên Y Vệ",
    genre: "Khoa Huyễn",
    read: 555550,
    chap: 624,
    img: "https://static.cdnno.com/poster/tan-the-ta-tu-mau-chot-so-nguoi-khac-them-mot-cai/150.jpg?1680454384",
    describe:
      "Dũng cảm, hèn mọn, thiện lương, gian xảo, khoan hậu, tham lam, ưu nhã, hung ác, vui vẻ, biến thái, chính trực, giả vờ chính đáng...Tại cái này tận thế đồng dạng thế giới, chỉ có tại dị tinh chiến trường thủ thắng mới có thể thu được lấy tư nguyên, cam đoan văn minh kéo dài.Mỗi cái tiến vào dị tinh chiến trường chiến sĩ, đều sẽ ngẫu nhiên thu hoạch được một cái thuộc về mình từ mấu chốt.Nói chuyện hành động phù hợp từ mấu chốt, các hạng thuộc tính liền sẽ phi tốc trưởng thành, thu hoạch được siêu nhân năng lực giống nhau, trái lại, người thiết lập sụp đổ, liền sẽ cấp tốc suy yếu;Đây là một cái liều diễn kỹ thế giới;"
  },
  {
    index: 5,
    name: "Tam Quốc: Ai Bảo Hắn Làm Mưu Sĩ?",
    author: "Tam Thiên Tứ Bao",
    genre: "Dã Sử",
    read: 27938,
    chap: 250,
    img: "https://static.cdnno.com/poster/tam-quoc-ai-bao-han-lam-muu-si/150.jpg?17014238584",
    describe:
      "Trương Hàn xuyên qua Hán mạt Tam quốc, không chỗ có thể đi lúc, dấn thân vào Tào doanh. Thức tỉnh 【 công thành hệ thống 】, chỉ cần lập công liền có thể đạt được ban thưởng, thế là Trương Hàn khổ luyện võ nghệ, anh dũng chém giết, rốt cục thông qua không ngừng lập công đem 【 vũ lực 】 tăng lên trên diện rộng về sau, ngang nhiên chuyển thành tâm tâm niệm niệm mưu thần!"
  },
  {
    index: 2,
    name: "Ai Bảo Ngươi Năng Lực Như Thế Dùng?",
    author: "Thái Bạch Thủy Quân",
    genre: "Huyền Huyễn",
    read: 156653,
    chap: 550,
    img: "https://static.cdnno.com/poster/ai-bao-nguoi-nang-luc-nhu-the-dung/150.jpg?1691777892",
    describe:
      "Toàn dân thức tỉnh thế giới bên trong, chư giới hội tụ thành bí cảnh, các Giác Tỉnh giả cho rằng bọn họ là Chư Thiên Vạn Giới trung tâm, thẳng đến bí cảnh xâm lấn, vương triều những năm cuối, thế giới đổ sụp các loại sự kiện lớn cho bọn hắn một cái vang dội bạt tai mạnh.. . .Ta phải tìm tới là ai đem ta một ngàn vạn biến thành một ngàn! Vương Lâm Trì bị ép phấn đấu sau nói như vậy."
  },
  {
    index: 3,
    name: "Lần Này Không Làm Nhà Huấn Luyện",
    author: "Kỵ Xa Đích Phong",
    genre: "Đồng Nhân",
    read: 70427,
    chap: 369,
    img: "https://static.cdnno.com/poster/lan-nay-khong-lam-nha-huan-luyen/150.jpg?1704308389",
    describe:
      "Naoki xuyên qua đến Pokémon thế giới kế thừa một nhà nông trường, cũng thu được dùng món ăn cho Pokémon mang đến thần kỳ lực lượng năng lực.Nông trường bên trong Pokémon trên thân bởi vậy sinh ra một chút biến hóa kỳ diệu.Có thể ba trăm sáu mươi độ không góc chết không sau dao sử dụng ra [ siêu cấp Rollout [ Lăn ] ] Miltank, tốc độ như Tật Phong Tấn Lôi những nơi đi qua đều là tàn ảnh Cyclizar, có thể một cái búa đánh bay Snorlax song đuôi ngựa siêu cấp đại lực sĩ Tinkaton. . ."
  },
  {
    index: 5,
    name: "Tam Quốc: Ai Bảo Hắn Làm Mưu Sĩ?",
    author: "Tam Thiên Tứ Bao",
    genre: "Dã Sử",
    read: 27938,
    chap: 250,
    img: "https://static.cdnno.com/poster/tam-quoc-ai-bao-han-lam-muu-si/150.jpg?17014238584",
    describe:
      "Trương Hàn xuyên qua Hán mạt Tam quốc, không chỗ có thể đi lúc, dấn thân vào Tào doanh. Thức tỉnh 【 công thành hệ thống 】, chỉ cần lập công liền có thể đạt được ban thưởng, thế là Trương Hàn khổ luyện võ nghệ, anh dũng chém giết, rốt cục thông qua không ngừng lập công đem 【 vũ lực 】 tăng lên trên diện rộng về sau, ngang nhiên chuyển thành tâm tâm niệm niệm mưu thần!"
  }
]

/// Account
// const nickname = ref("Đào Xuân Đông")
const description = ref("I am a student")

const currentExp = ref(12345)
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

defineProps<{
  profile: string
}>()
const current = ref(1)
const max = ListNovels.length / 5
const data = computed(() => {
  const itemsPerPage = 5
  const startIndex = (current.value - 1) * itemsPerPage
  const endIndex = startIndex + itemsPerPage
  return ListNovels.slice(startIndex, endIndex)
})
</script>
<style>
.img-novel {
  box-shadow: 4px 4px 6px rgba(0, 0, 0, 0.3);
}
.img-novel:hover {
  opacity: 200;
  cursor: pointer;
}
.name-novel:hover {
  color: rgb(218, 110, 27);
  cursor: pointer;
}

.swiper {
  width: 100%;
  height: 30%;
}

.swiper-slide {
  text-align: center;
  font-size: 18px;
  background: #f5ebeb;

  /* Center slide text vertically */
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
