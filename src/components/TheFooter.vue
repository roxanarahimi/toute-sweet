<template>
  <footer class="main-bg text-light w-100 container-fluid">
    <div class="row px-2 px-xl-5 justify-content-xl-between h-100">
      <div class="col-md-6 col-xl-3 mb-3 mb-xl-0 h-100 text-center">
        <img src="/img/logoW.png" class=" mt-3" width="200px" alt="">
        <p class="text-justify px-xl-3">
          لورم ایپسوم متن ساختگی با تولید سادگی نامفهوم از صنعت چاپ و با استفاده از طراحان گرافیک است چاپگرها و متون
          بلکه روزنامه و مجله در ستون و سطرآنچنان که لازم است و برای شرایط فعلی تکنولوژی مورد نیاز و کاربردهای.
        </p>
      </div>
      <div class="col-md-6 col-xl-3 px-xl-3 mb-3 d-grid">
        <div class="align-self-end">
          <p class="text-center mb-4"><b>تماس با ما</b></p>
          <ul class="p-0">
            <li class="d-flex mb-3">
                <span class="me-2">
                  <img src="/img/bi-geo-alt.svg" class="" alt="">
                </span>
              <small>
                <p class="text-justify">
                  نشانی کارخانه: استان البرز، جاده ملارد، بلوار نیروگاه، ناحیه صنعتی نور، خیابان نور، کوچه نور سوم غربی، پلاک 18
                </p>
              </small>
            </li>
            <li class="d-flex mb-3">
                <span class="me-2">
                  <img src="/img/bi-telephone.svg" alt="">
                </span>
              <small dir="ltr">
                <a href="tel:+982636660925" dir="rtl">تلفن: <span  dir="ltr">026 36660925</span></a>

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
      <div class="col-12 px-2 px-xl-3 mt-xl-3 mb-3">
        <small>
          &copy; کلیه حقوق این وبسایت متعلق به شرکت
          <span style=" white-space: nowrap;">تژبهدان سریرا</span>
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