<template>
  <q-page class="max-w-1200px mx-auto">
    <div class="text-20px text-bold m-2 opacity-90">
      Những câu hỏi thường gặp
    </div>
    <div class="opacity-80">
      <q-expansion-item
        :label="'Làm sao đổi màu nền, cỡ chữ, font chữ'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div class="mx-2 py-1 cursor-pointer">
          <p>
            - Dùng web trên máy tính: ấn vào nút bánh răng ở bên trái khung đọc
            truyện. Video hướng dẫn:
            <span class="text-italic"
              >https://static.cdnno.com/videos/howto/setting-desktop.mp4</span
            ><br />
            - Dùng web trên điện thoại: ấn vào giữa nội dung chương truyện rồi
            ấn nút bánh răng ở bên dưới. Video hướng dẫn:
            <span class="text-italic"
              >https://static.cdnno.com/videos/howto/setting-mobile.mp4</span
            >
            <br />
            - Dùng app Mê Truyện Chữ - Nữ Hiệp trên điện thoại: ấn vào giữa nội
            dung chương truyện rồi chọn Cài đặt. Vdeo hướng dẫn:
            <span class="text-italic"
              >https://static.cdnno.com/videos/howto/setting-app.mp4</span
            ><br />

            <br />Tips: ở trên app ngoài cài đặt màu nền, cỡ chữ, font chữ bạn
            còn có thể cài đặt chế độ đọc truyện theo Lật trang hoặc Cuộn dọc, ở
            chế độ Lật trang bạn có thể ấn vào mép phải màn hình để lật trang
            thay vì vuốt
          </p>
        </div>
      </q-expansion-item>

      <q-expansion-item
        :label="'Hoa là gì và dùng để làm gì?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse2"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Hoa là một loại phiếu đề cử, dùng để đề cử truyện bạn thích, giúp
            cho nhiều người biết đến truyện đó hơn và hỗ trợ người đăng truyện.
            Truyện càng được đề cử nhiều Hoa thì đang có thứ hạng tốt trên Bảng
            Xếp Hạng
          </div>
        </div>
      </q-expansion-item>
      <q-expansion-item
        :label="'Làm sao để có Hoa?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse3"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Hoa được cộng tự động vào tài khoản của bạn vào lúc 0h00 hàng ngày,
            số lượng nhận được tùy vào Đẳng Cấp của bạn.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Hoa tồn tại được bao lâu?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse4"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Hoa phải sử dụng ngay trong ngày, nếu không sẽ tàn và không sử dụng
            được nữa.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Quy định khi tặng Hoa'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse5"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Để có sự công bằng nhất, mỗi người chỉ được sử dụng 1 tài khoản.
            Chúng tôi sẽ tổng kết và đánh giá tất cả những đề cử Hoa cho truyện,
            nếu phát hiện sử dụng nhiều tài khoản để lấy hoa đề cử, truyện sẽ bị
            trừ số hoa đề cử g·ian l·ận, tất cả tài khoản sẽ bị khóa.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Kẹo là gì và để làm gì?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse6"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Kẹo là một loại vật phẩm trong website. Kẹo dùng để tặng quà cho
            người đăng truyện, mở khóa chương
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Làm sao để có Kẹo?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse7"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Bạn có thể có kẹo qua hai hình thức: <br /><br />- Làm nhiệm vụ hàng
            ngày để nhận thưởng, trong phần Cá nhân - Nhận thưởng <br />- Mua
            kẹo trong Cá nhân - Mua kẹo. Có thể mua kẹo thông qua momo, zalopay,
            ngân hàng, paypal hoặc đổi mã thẻ, mã thẻ có thể là mã nhận được khi
            tham gia event hoặc mã thẻ cào
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Kẹo thường và Kẹo miễn phí khác nhau như nào?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse8"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Kẹo thường có được khi bạn đổi mã hoặc mua kẹo. Kẹo thường hạn sử
            dụng lâu: 30 năm<br />Kẹo miễn phí có được khi bạn làm nhiệm vụ hoặc
            tặng kèm khi bạn đổi mã lấy Kẹo thường. Kẹo miên phí thường nhanh
            hết hạn: từ vài ngày đến vài tuần
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi muốn biết đang có bao nhiêu Kẹo, hạn sử dụng, đã sử dụng như nào thì phải làm sao?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse9"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">Bạn có thể vào mục Cá nhân - Tài sản để xem</div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi có thể chuyển Kẹo cho người khác dù người đó không có đăng truyện hay không?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse10"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Không!<br /><br />Kẹo chỉ dùng tặng quà và mở khóa chương.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Quy định về lạm dụng Kẹo miễn phí'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse11"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Cũng như Hoa, chúng tôi sẽ tổng kết và đánh giá tất cả những món quà
            tặng ở trong từng truyện, nếu phát hiện l·ạm d·ụng nhiều tài khoản
            để "cày" Kẹo miễn phí, tất cả tài khoản sẽ bị khóa, Kẹo tặng sẽ bị
            trừ.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Mấy thứ Cấp này nọ là gì vậy?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse12"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Cấp là 1 cách để vinh danh các thành viên tích cực của web. Bạn càng
            hoạt động tích cực cấp càng cao, lợi ích nhận được càng lớn
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Chà, nghe cũng hấp dẫn, thế Cấp có tác dụng gì?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse13"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Cấp càng cao càng nổi bật giữa đám dân thường khi bình luận hay đánh
            giá nè<br /><br />Cấp càng cao càng nhận được nhiều Hoa hàng ngày
            nè, cụ thể:<br /><br />- Cấp 1: nhận được 1 Hoa hàng ngày<br />- Cấp
            2: nhận được 2 Hoa hàng ngày<br />- Cấp 3: nhận được 3 Hoa hàng
            ngày<br />- Cấp 4: nhận được 4 Hoa hàng ngày<br />- Cấp 5: nhận được
            5 Hoa hàng ngày
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Làm sao để lên cấp vậy?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse14"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Bạn có thể lên cấp sau khi đã đủ kinh nghiệm, còn điểm kinh nghiệm
            làm sao để có thì tất nhiên là làm nhiệm vụ để có rồi. Với mỗi cấp
            bạn cần số điểm kinh nghiệm như sau<br /><br />- Cấp 1: 10 Exp<br />-
            Cấp 2: 100 Exp<br />- Cấp 3: 500 Exp<br />- Cấp 4: 2.000 Exp<br />-
            Cấp 5: 10.000 Exp
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Đừng để bị trừ Exp'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse15"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Khi đánh giá và bình luận truyện bạn phải tuân thủ quy định của
            website, nếu vi phạm sẽ bị dính thẻ Phạt, để tẩy thẻ Phạt bạn sẽ mất
            Exp, nếu không có Exp thì tài khoản của bạn sẽ có thể bị khóa một
            thời gian để được tẩy thẻ Phạt
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Người hâm mộ là gì, sao tôi đọc truyện nhưng không được thành người hâm mộ?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse16"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Bạn đọc 1 truyện, bạn yêu thích truyện đó nhưng bạn không được thành
            người hâm mộ của truyện? Chỉ đọc truyện chưa thể hiện hết sự yêu
            thích của bạn dành cho truyện, bạn cần phải hành động, phải tặng
            hoa, tặng quà cho truyện thì bạn mới trở thành người hâm mộ của
            truyện
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Làm sao để tăng điểm hâm mộ?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse17"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            · Tiêu xài 1 Kẹo = 1 điểm hâm mộ (trả phí đọc, tặng quà)<br />· Tặng
            1 Hoa = 1000 điểm hâm mộ<br /><br />Bạn tặng càng nhiều càng được
            nhiều điểm, điểm càng cao bạn càng có vị trí cao trong bảng xếp hạng
            người hâm mộ
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi muốn xem điểm hâm mộ của mình, vào đâu để xem?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse18"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Vào truyện bạn muốn xem, ấn vào tab Hâm mộ, nếu bạn có điểm cao, bạn
            sẽ nằm ngay ở bảng xếp hạng, nếu điểm còn thấp bạn kéo xuống dưới sẽ
            thấy. Nếu dùng app điểm Hâm mộ nằm dưới thông tin truyện
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Làm sao để tặng quà? Tặng hoa? Thả cảm xúc?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse19"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Để Tặng Hoa hoặc Tặng Quà vào bất cứ chương truyện nào của truyện
            bạn muốn tặng, bạn sẽ thấy các nút:<br />- Tặng Quà, chọn món quà
            phù hợp với sở thích và túi Kẹo của mình sau đó ấn Tặng<br />- Tặng
            Hoa<br /><br /><br />Để thả cảm xúc:<br />- Trên app Mê Truyện Chữ:
            kéo xuống cuối chương<br />- Trên web dùng máy tính, nút trái tim
            góc dưới bên phải<br />- Trên web dùng điện thoại, ấn giữa màn hình
            đọc truyện
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Check-in để làm gì? Làm sao để check-in?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse20"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            - Check-in là một loại nhiệm vụ hàng ngày. Khi check-in bạn sẽ nhận
            được Kẹo và Exp, nếu bạn chịu khó check-in đều đặn liên tục bạn còn
            nhận được quà ngoài định mức<br />- Bạn cần có các hoạt động trên
            web như bình luận, like, ... mới có thể check-in
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Số liệu Đã đọc trong đánh giá truyện là gì?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse21"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            - Để đánh giá truyện tất nhiên bạn phải đọc truyện đó rồi mới có thể
            đánh giá được. <br /><br />- Số liệu "Đã đọc" thể hiện người đánh
            giá đã đọc bao nhiêu chương trong truyện đó rồi, số "Đã đọc" càng
            lớn thì đánh giá càng có tính chính xác cao hơn. Nếu chỉ mới đọc vài
            chương đã đánh giá thì tất nhiên đánh giá đó không đáng tin cho lắm
            rồi.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi thấy số Đã đọc trong đánh giá của tôi không chính xác?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse22"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
          style=""
        >
          <div class="p-3">
            Cái này có thể do nhiều nguyên nhân:<br /><br />- Bạn đọc ở phiên
            bản cũ (truyencv) thì không được tính ở đây<br />- Bạn đọc mà quên
            không đăng nhập tài khoản<br />....
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi có làm gì đâu mà bị thêm thẻ phạt?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse24"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Khi bạn có bình luận hoặc đánh giá không phù hợp hoặc vi phạm nội
            quy, bị người đọc khác báo cáo (gắn cờ), biên tập viên sẽ xem báo
            cáo và nội dung bình luận, đánh giá của bạn, nếu nội dung không vi
            phạm bạn sẽ không bị thêm thẻ phạt nhưng nếu có vi phạm, tùy vào mức
            độ vi phạm bạn sẽ bị thêm số thẻ phạt tương ứng.<br /><br />Rất khó
            có trường hợp bạn bị thẻ phạt oan vì ít nhất phải có 02 người xác
            nhận nội dung bình luận, đánh giá của bạn vi phạm thì bạn mới bị thẻ
            phạt: người báo cáo bạn và biên tập viên kiểm tra báo cáo.
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Vì sao tôi bị khóa nick?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse25"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Bạn có thể xem lý do bị khóa nick khi đăng nhập vào web/app. Với lý
            do: vi phạm hoặc bị tố cáo quá nhiều tức là bạn đã bị trên 100 thẻ
            phạt và hệ thống tự khóa nick với số ngày tương ứng
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="' Vì sao tôi và người khác chửi lộn mà chỉ mình tôi bị khóa?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse26"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            - Thứ nhất làm sao bạn biết chỉ mình bạn bị khóa nick? Cách đơn giản
            nhất để kiểm tra là bạn xem bình luận, đánh giá vi phạm của người
            kia đối với bạn đã bị xóa chưa, bị xóa rồi tức là người kia cũng đã
            bị xử lý.<br />- Nếu thấy bình luận, đánh giá của người kia chưa bị
            xử lý thì bạn vui lòng đọc lại câu hỏi: Tôi có làm gì đâu mà bị thẻ
            phạt? bạn sẽ hiểu là biên tập viên chỉ kiểm tra các bình luận, đánh
            giá bị báo cáo (gắn cờ) nếu bình luận, đánh giá của người khác vi
            phạm nhưng không ai báo cáo thì biên tập viên cũng không biết mà xử
            lý, vì thế nếu thấy vẫn còn bình luận, đánh giá vi phạm thì bạn hãy
            báo cáo cho biên tập viên để được xử lý
          </div>
        </div> </q-expansion-item
      ><q-expansion-item
        :label="'Tôi còn thắc mắc khác?'"
        header-class="text-16px text-bold"
        group="help"
        class="w-100%"
      >
        <div
          id="collapse27"
          aria-labelledby="headingOne"
          data-parent="#faqs"
          class="collapse"
        >
          <div class="p-3">
            Bạn có thể vào Liên hệ quản trị viên (trên web) hoặc Liên hệ, báo
            lỗi (trên app) để đặt câu hỏi
          </div>
        </div>
      </q-expansion-item>
    </div>
  </q-page>
</template>
<script lang="ts" setup></script>
