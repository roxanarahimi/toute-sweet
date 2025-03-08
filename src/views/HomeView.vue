<template>
  <div id="header" class="">
    <nav class="navbar navbar-expand-lg">
      <div class="container-fluid d-flex justify-content-between">
        <div class="d-none d-lg-block">
          <a class="navbar-brand" href="#"><img src="/img/logoW.png" width="100px" alt=""></a>
        </div>
        <div class="navbar-toggler text-light border-0 cursor"  data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown"
             aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
          <i class="bi bi-list h1"></i>
        </div>
        <div class="d-lg-none">
          <a class="navbar-brand" href="#"><img src="/img/logoW.png" width="100px" alt=""></a>
        </div>
        <div class="collapse navbar-collapse justify-content-center" id="navbarNavDropdown">
          <ul class="navbar-nav text-center">
            <li class="nav-item px-3">
              <router-link to="/" class="nav-link active" aria-current="page" href="#">خانه</router-link>
            </li>
            <li class="nav-item px-3">
              <a class="nav-link" href="#">محصولات</a>
            </li>
            <li class="nav-item px-3">
              <a class="nav-link" href="#">درباره ما</a>
            </li>
            <li class="nav-item px-3">
              <a class="nav-link" href="#">تماس با ما</a>
            </li>
          </ul>
        </div>

        <div class="d-none d-lg-block">
          <a class="navbar-brand" href="#"><i class="bi bi-search"></i></a>
        </div>
      </div>
    </nav>
    <div class="w-100">
      <img src="img/banner.jpg" width="100%" alt="">
    </div>
  </div>

  <main class="container-fluid">

    <div id="categories" class="w-100 d-flex justify-content-between justify-content-md-center py-5 mb-5">
      <div v-for="cat in categories" class="cat-box-wrapper mx-md-3">
        <div class="cat-box" @click="filterProducts(cat.id)">
          <img :src="cat.image" width="100%" alt="">
          <p class="cat-title">{{ cat.title }}</p>
        </div>
      </div>
    </div>

    <div id="products" class="w-100 p-0 m-0 px-0 px-md-5 row">
      <router-link :to="'/product/'+pro.id" v-for="pro in products" class="product-box-wrapper" :class="{'col-12 col-lg-4':catFilter, 'col-6 col-lg-2':!catFilter}">
        <div class="product-box">
          <img :src="pro.image" width="100%" alt="">
          <p class="product-title">{{ pro.title }}</p>
        </div>
      </router-link>
    </div>
  </main>
  <footer class="main-bg text-light w-100 container-fluid">
    <div class="px-lg-5 ftr" style="padding-top: 100px">
      <div class="row px-5 justify-content-xl-between">
        <div class="col-lg-5 col-xl-5 row mb-4">
          <div class="col-12 px-lg-3 ftr-i" style="">
            <p class="text-center mb-4"><b>تماس با ما</b></p>

            <ul class="p-0">
              <li class="d-flex mb-3">
            <span class="me-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-geo-alt"
                   viewBox="0 0 16 16">
                <path
                    d="M12.166 8.94c-.524 1.062-1.234 2.12-1.96 3.07A31.493 31.493 0 0 1 8 14.58a31.481 31.481 0 0 1-2.206-2.57c-.726-.95-1.436-2.008-1.96-3.07C3.304 7.867 3 6.862 3 6a5 5 0 0 1 10 0c0 .862-.305 1.867-.834 2.94zM8 16s6-5.686 6-10A6 6 0 0 0 2 6c0 4.314 6 10 6 10z"/>
                <path d="M8 8a2 2 0 1 1 0-4 2 2 0 0 1 0 4zm0 1a3 3 0 1 0 0-6 3 3 0 0 0 0 6z"/>
              </svg>
            </span>
                <small>
                  <a target="_blank"
                     href="https://www.google.com/maps/place/AmadehLaziz/@35.7302329,51.3807302,19z/data=!4m6!3m5!1s0x3f8e07d020c7ca45:0x43bf4c9a730015f3!8m2!3d35.7301399!4d51.3807224!16s%2Fg%2F11c1r04p2q">
                    دفتر مرکزی: تهران، خیابان گیشا، خیابان هشتم، پلاک 58</a>
                </small>
              </li>
              <li class="d-flex mb-3">
            <span class="me-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-telephone"
                   viewBox="0 0 16 16">
                <path
                    d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.568 17.568 0 0 0 4.168 6.608 17.569 17.569 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.678.678 0 0 0-.58-.122l-2.19.547a1.745 1.745 0 0 1-1.657-.459L5.482 8.062a1.745 1.745 0 0 1-.46-1.657l.548-2.19a.678.678 0 0 0-.122-.58L3.654 1.328zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"/>
              </svg>
           </span>

                <small dir="ltr">
                  <a href="tel:+982636670558">+98 26 36670558</a>

                </small>
              </li>
              <li class="d-flex mb-3">
            <span class="me-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-telephone"
                   viewBox="0 0 16 16">
                <path
                    d="M3.654 1.328a.678.678 0 0 0-1.015-.063L1.605 2.3c-.483.484-.661 1.169-.45 1.77a17.568 17.568 0 0 0 4.168 6.608 17.569 17.569 0 0 0 6.608 4.168c.601.211 1.286.033 1.77-.45l1.034-1.034a.678.678 0 0 0-.063-1.015l-2.307-1.794a.678.678 0 0 0-.58-.122l-2.19.547a1.745 1.745 0 0 1-1.657-.459L5.482 8.062a1.745 1.745 0 0 1-.46-1.657l.548-2.19a.678.678 0 0 0-.122-.58L3.654 1.328zM1.884.511a1.745 1.745 0 0 1 2.612.163L6.29 2.98c.329.423.445.974.315 1.494l-.547 2.19a.678.678 0 0 0 .178.643l2.457 2.457a.678.678 0 0 0 .644.178l2.189-.547a1.745 1.745 0 0 1 1.494.315l2.306 1.794c.829.645.905 1.87.163 2.611l-1.034 1.034c-.74.74-1.846 1.065-2.877.702a18.634 18.634 0 0 1-7.01-4.42 18.634 18.634 0 0 1-4.42-7.009c-.362-1.03-.037-2.137.703-2.877L1.885.511z"/>
              </svg>
           </span>

                <small dir="ltr">
                  <a href="tel:+982141638000">+98 21 41638000</a>

                </small>
              </li>
              <li class="d-flex mb-3">
            <span class="me-2">
             <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-envelope"
                  viewBox="0 0 16 16">
  <path
      d="M0 4a2 2 0 0 1 2-2h12a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2zm2-1a1 1 0 0 0-1 1v.217l7 4.2 7-4.2V4a1 1 0 0 0-1-1zm13 2.383-4.708 2.825L15 11.105zm-.034 6.876-5.64-3.471L8 9.583l-1.326-.795-5.64 3.47A1 1 0 0 0 2 13h12a1 1 0 0 0 .966-.741M1 11.105l4.708-2.897L1 5.383z"/>
</svg>
           </span>

                <small dir="ltr">
                  <a href="mailto:info@copacafe.co">info@copacafe.co</a>

                </small>
              </li>
              <li class="d-flex mb-3">
            <span class="me-2">
             <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-postcard"
                  viewBox="0 0 16 16">
  <path fill-rule="evenodd"
        d="M2 2a2 2 0 0 0-2 2v8a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2H2ZM1 4a1 1 0 0 1 1-1h12a1 1 0 0 1 1 1v8a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V4Zm7.5.5a.5.5 0 0 0-1 0v7a.5.5 0 0 0 1 0v-7ZM2 5.5a.5.5 0 0 1 .5-.5H6a.5.5 0 0 1 0 1H2.5a.5.5 0 0 1-.5-.5Zm0 2a.5.5 0 0 1 .5-.5H6a.5.5 0 0 1 0 1H2.5a.5.5 0 0 1-.5-.5Zm0 2a.5.5 0 0 1 .5-.5H6a.5.5 0 0 1 0 1H2.5a.5.5 0 0 1-.5-.5ZM10.5 5a.5.5 0 0 0-.5.5v3a.5.5 0 0 0 .5.5h3a.5.5 0 0 0 .5-.5v-3a.5.5 0 0 0-.5-.5h-3ZM13 8h-2V6h2v2Z"/>
</svg>
           </span>

                <small dir="ltr" style="cursor: pointer;position: relative" @click="coppyCode">
                  کد پستی:

                  <span id="postalcode">
                      1446863914
                    </span>
                  <!--                  <span id="coppyAlert">-->
                  <!--                      کپی شد!-->
                  <!--                    </span>-->
                </small>
              </li>


            </ul>
          </div>
        </div>
        <div class="col-lg-7 col-xl-6 px-3 d-grid">
          <div class=" justify-content-between align-self-end d-none d-md-flex">
            <div><img src="/img/c1.png" class="footer-img" alt=""></div>
            <div><img src="/img/c2.png" class="footer-img" alt=""></div>
            <div><img src="/img/c4.png" class="footer-img" alt=""></div>
            <div><img src="/img/c3.png" class="footer-img" alt=""></div>
          </div>
          <div class="d-md-none d-flex">
            <div class="p-2"><img src="/img/c1.png" class="footer-img " alt=""></div>
            <div class="p-2"><img src="/img/c3.png" class="footer-img " alt=""></div>
          </div>
          <div class="d-md-none d-flex">
            <div class="p-2"><img src="/img/c2.png" class="footer-img " alt=""></div>
            <div class="p-2"><img src="/img/c4.png" class="footer-img " alt=""></div>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-12">
          <small class="d-block m-3 mx-5">
            &copy; کلیه حقوق این وبسایت متعلق به شرکت
            <br class="d-sm-none">
            آماده لذیذ میباشد.
          </small>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

import {onMounted, ref} from "vue";

export default {
  name: 'HomeView',
  components: {},
  setup() {
    const categories = [
      {id: 1, image: '/img/گرانولابار-نارگیل.png', title: 'انرژی بار'},
      {id: 2, image: '/img/موسلی-نارگیل-و-شکلات-تلخ.png', title: 'موسلی'},
      {id: 3, image: '/img/پروتیین-بار-فندق.png', title: 'پروتئین بار سوفیت'},
    ];
    const pros = [
      {id:1,cat_id: 1, image: '/img/گرانولابار دانه و کشمش.png', title: 'گرانولابار دانه و کشمش', text: ''},
      {id:2,cat_id: 1, image: '/img/گرانولابار دانه-چیا.png', title: 'گرانولابار دانه چیا', text: ''},
      {id:3,cat_id: 1, image: '/img/گرانولابار-بادام-زمینی.png', title: 'گرانولابار بادام زمینی', text: ''},
      {id:4,cat_id: 1, image: '/img/گرانولابار-نارگیل.png', title: 'گرانولابار نارگیل', text: ''},
      {id:5,cat_id: 1, image: '/img/گرانولابار-کرنبری.png', title: 'گرانولابار کرنبری', text: ''},
      {id:6,cat_id: 2, image: '/img/موسلی-زردالو.png', title: 'موسلی زردالو', text: ''},
      {id:7,cat_id: 2, image: '/img/موسلی-سیب-و-دارچین.png', title: 'موسلی سیب و دارچین', text: ''},
      {id:8,cat_id: 2, image: '/img/موسلی-نارگیل-و-شکلات-تلخ.png', title: 'موسلی‌نارگیل و شکلات‌تلخ', text: ''},
      {id:9,cat_id: 2, image: '/img/موسلی-کرنبری.png', title: 'موسلی کرنبری', text: ''},
      {id:10,cat_id: 2, image: '/img/موسلی-کره-بادام-زمینی.png', title: 'موسلی کره بادام زمینی', text: ''},
      {id:11,cat_id: 3, image: '/img/پروتیین-بار-فندق.png', title: 'پروتئین بار فندق', text: ''},
      {id:12,cat_id: 3, image: '/img/پروتیین-بار-موزی.png', title: 'پروتئین بار موزی', text: ''},
      {id:13,cat_id: 3, image: '/img/پروتیین-بار-پرتغال.png', title: 'پروتئین بار پرتغال', text: ''},
      {id:14,cat_id: 3, image: '/img/پروتیین-بار-کارامل.png', title: 'پروتئین بار کارامل', text: ''},

    ];
    const products = ref([]);
    const catFilter = ref(false);
    onMounted(() => {
      window.scrollTo({ top: 0, behavior: 'smooth' });
      products.value = pros;
    })
    const filterProducts = (id) => {
      catFilter.value = true;
      products.value = [];
      products.value = pros.filter((element) => {
        return element.cat_id === id;
      })
    }
    return {
      products, categories, pros, filterProducts, catFilter
    }
  }
}
</script>
