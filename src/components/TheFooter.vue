<template>
  <footer id="footer" class="main-bg text-light w-100 container-fluid">
    <div class="row px-2 px-xl-5 justify-content-xl-between h-100">
      <div class="col-md-6 col-xl-5 mb-xl-0 h-100 text-center ">
        <img src="/img/logoW.png" class="mb-4 mb-xl-0 mt-3" width="200px" alt="">
        <p class="text-justify px-xl-3">

          شرکت «تژ به‌دان سریرا» با برند تجاری TouteSweet از سال ۱۳۹۷ در زمینه تولید انواع موسلی، پروتئین‌بار و
          انرژی‌بار فعالیت خود را آغاز کرده است. هدف اصلی ما ارائه مواد غذایی سالم و مغذی است که مناسب برای تمام
          گروه‌های سنی بوده و تجربه‌ای لذت‌بخش از تغذیه سالم را به مشتریان ارائه دهد. در تژ به‌دان سریرا، ما به تغذیه
          سالم به‌عنوان یکی از ارکان اصلی زندگی توجه ویژه‌ای داریم و تمامی تلاش خود را در جهت ارتقای سلامت و بهبود کیفیت
          زندگی افراد متمرکز کرده‌ایم.</p>
      </div>
      <div class="col-md-6 col-xl-4 px-xl-3 mb-5 mb-xl-3 d-grid ">
        <div class="align-self-end">
          <p class="text-center mt-5 mt-xl-0 mb-4"><b>تماس با ما</b></p>
          <ul class="p-0">
            <li class="d-flex mb-3">
                <span class="me-2">
                  <img src="/img/bi-geo-alt.svg" class="" alt="">
                </span>
              <small>
                <p class="text-justify">
                  نشانی کارخانه: استان البرز، جاده ملارد، بلوار نیروگاه، ناحیه صنعتی نور، خیابان نور، کوچه نور سوم غربی،
                  پلاک 18
                </p>
              </small>
            </li>
            <li class="d-flex mb-3">
                <span class="me-2">
                  <img src="/img/bi-telephone.svg" alt="">
                </span>
              <small dir="ltr">
                <a href="tel:+982636660925" dir="rtl">تلفن: <span dir="ltr">026 36660925</span></a>

              </small>
            </li>
            <!--              <li class="d-flex mb-3">-->
            <!--                <span class="me-2">-->
            <!--                  <img src="/img/bi-envelope.svg" alt="">-->
            <!--                </span>-->
            <!--                <small dir="ltr">-->
            <!--                  <a href="mailto:info@copacafe.co">info@copacafe.co</a>-->
            <!--                </small>-->
            <!--              </li>-->
            <li class="d-flex mb-3">
                <span class="me-2">
                  <img src="/img/bi-postcard.svg" alt="">
                </span>

              <small dir="ltr" style="cursor: pointer;position: relative" @click="coppyCode">
                کد پستی:
                <span id="postalcode">
                      3167654917
                  </span>
                <!--                  <span id="coppyAlert">-->
                <!--                      کپی شد!-->
                <!--                    </span>-->
              </small>
            </li>


          </ul>
        </div>

      </div>
      <div class="col-12 px-2 px-xl-3 mt-xl-3 mb-3 ">
        <small>
          &copy; کلیه حقوق این وبسایت متعلق به شرکت
          <span style=" white-space: nowrap;">تژ به‌دان سریرا</span>
          میباشد.
        </small>
      </div>

    </div>

  </footer>
</template>

<script>
export default {
  name: "TheFooter"
}
</script>

<style scoped>

</style>