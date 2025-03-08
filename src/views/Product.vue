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
  </div>

  <main>
    <div class="w-100 main-bg row m-0 p-0 justify-content-center py-5">
      <div class="col-10 row m-0 p-0 justify-content-center justify-content-md-start">
        <div class="col-10 mb-5 mb-md-0 col-md-4 main-bg-light rounded">
          <img :src="product.image" class="w-100" alt="">
        </div>
        <div class="col-md-8 text-light text-start d-grid">
          <div class="align-self-end text-center text-md-start ps-md-5">
            <h1 class="fw-bolder mb-4">{{ product.title }}</h1>
            <h2>{{ product.subTitle }}</h2>
            <h3>{{ product.contains }}</h3>
            <h5>{{ product.sugar }}</h5>
          </div>
        </div>
      </div>

    </div>

<!--    <div class="row" style="background-image: url('/img/nuts.png')">-->
   <div class="">
<!--     <img src="/img/nuts.png" width="100%" alt="">-->
<!--     <div class="d-grid h-100 w-100 " style="position: absolute; top:0; right:0">-->
     <div class="d-grid h-100 w-100 " >
       <div class="align-self-center w-100">
         <div class="row ">
           <div class="mt-5 px-5 d-md-none">
             <strong>جدول ارزش غذایی {{ product.title }} در {{ product.weight }} گرم</strong>
             <table class="table border mt-3">
               <tbody>
               <tr>
                 <th scope="col" class="ps-3">انرژی</th>
                 <td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.energy }} Kcal</td>
               </tr>
               <tr>
                 <th scope="col" class="ps-3">پروتئین</th>
                 <td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.protein }} g</td>
               </tr>
               <tr>
                 <th scope="col" class="ps-3">کربوهیدرات</th>
                 <td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.carbohydrate}} g</td>
               </tr>
               <tr>
                 <th scope="col" class="ps-3">چربی</th>
                 <td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.fat}} g</td>
               </tr>
               <tr>
                 <th scope="col" class="ps-3">فیبر</th>
                 <td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.fiber}} g</td>
               </tr>
               </tbody>
             </table>
           </div>
           <div class="col-md-7 d-none d-md-block text-center text-md-start">
             <div class="w-100 mt-5 px-3 px-md-5 mb-5">
               <strong>جدول ارزش غذایی {{ product.title }} در {{ product.weight }} گرم</strong>
               <table class="table table-responsive border text-center mt-3 w-100">
                 <thead>
                 <tr>
                   <th scope="col">انرژی</th>
                   <th scope="col">پروتئین</th>
                   <th scope="col">کربوهیدرات</th>
                   <th scope="col">چربی</th>
                   <th scope="col">فیبر</th>
                 </tr>
                 </thead>
                 <tbody>
                 <tr>
                   <td dir="ltr">{{ product.nutritional_value?.energy }} Kcal</td>
                   <td dir="ltr">{{ product.nutritional_value?.protein }} g</td>
                   <td dir="ltr">{{ product.nutritional_value?.carbohydrate}} g</td>
                   <td dir="ltr">{{ product.nutritional_value?.fat}} g</td>
                   <td dir="ltr">{{ product.nutritional_value?.fiber}} g</td>
                 </tr>
                 </tbody>
               </table>
             </div>
             <div class="w-100 px-3 px-md-5 mb-5">
               <strong>ترکیبات</strong>
               <p class="text-justify w-100">{{ product.ingredients }}</p>
             </div>
           </div>
         </div>

       </div>


     </div>

     <div class="w-100  text-center text-md-start px-3 px-md-5">
       <strong>محصولات مشابه</strong>
       <div id="same-products" class="w-100 p-0 m-0 row mt-3">
         <a :href="'/product/'+pro.id" :key="pro.id" v-for="pro in sameProducts" class="product-box-wrapper col-6 col-md-3 col-lg-2">
           <div class="product-box">
             <img :src="pro.image" width="100%" alt="">
             <p class="product-title">{{ pro.title }}</p>
           </div>
         </a>
       </div>
     </div>
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
import {onMounted, ref} from "vue";
import {useRoute} from "vue-router/dist/vue-router";

export default {
  name: "Product",
  setup() {

    const route = useRoute();

    const pros = [
      {
        id: 1, cat_id: 1, image: '/img/گرانولابار دانه و کشمش.png',
        title: 'گرانولابار دانه و کشمش',
        subTitle: 'با کشمش و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، خرما، عسل، کشمش، مغز تخم آفتابگردان، مغز تخم کدو، غلات فرآوری شده گندم و ذرت، طعم‌دهنده طبیعی مجاز خوراکی، روغن کنجد، روغن نارگیل',
        nutritional_value: {
          energy: '122.6', carbohydrate: '23.71', protein: '3.5', fat: '1.72', fiber: '1.96'
        }
      },
      {
        id: 2, cat_id: 1, image: '/img/گرانولابار دانه-چیا.png',
        title: 'گرانولابار دانه چیا',
        subTitle: 'با دانه چیا و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، خرما، عسل، دانه چیا، غلات فرآوری شده گندم و ذرت، کنجد، فندق، مغز تخم آفتابگردان، روغن نارگیل، هل، زنجبیل، طعم‌دهنده مشابه طبیعی لیمو، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '130.83', carbohydrate: '22.85', protein: '3.46', fat: '3.19', fiber: '2.13'
        }
      },
      {
        id: 3, cat_id: 1, image: '/img/گرانولابار-بادام-زمینی.png',
        title: 'گرانولابار بادام زمینی',
        subTitle: 'با کره بادام زمینی و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 12% پروتئین',
        weight: 45,
        ingredients: 'جو پرک، جو دوسر پرک، عسل، کره بادام زمینی، غلات فرآوری شده گندم و ذرت، بادام زمینی، روغن کنجد، دارچین، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '197.1', carbohydrate: '28.12', protein: '5.53', fat: '7.87', fiber: '1'
        }
      },
      {
        id: 4, cat_id: 1, image: '/img/گرانولابار-نارگیل.png',
        title: 'گرانولابار نارگیل',
        subTitle: 'با نارگیل و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، عسل، پودر نارگیل، غلات فرآوری شده گندم و ذرت، مغز تخم آفتابگردان، کنجد، فندق، روغن نارگیل، روغن کنجد، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '147.14', carbohydrate: '21.24', protein: '3.29', fat: '6.14', fiber: '1.92'
        }
      },
      {
        id: 5, cat_id: 1, image: '/img/گرانولابار-کرنبری.png',
        title: 'گرانولابار کرنبری',
        subTitle: 'با کرنبری و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 9% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، کرنبری، غلات فرآوری شده گندم و ذرت، خرما، بادام، ارده، روغن نارگیل، تمشک، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '137.9', carbohydrate: '26.4', protein: '3', fat: '2.5', fiber: '1'
        }
      },
      {
        id: 6, cat_id: 2, image: '/img/موسلی-زردالو.png',
        title: 'موسلی زردالو',
        subTitle: 'با زردآلو و کشمش',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آهن، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، زردآلو، فندق، کشمش',
        nutritional_value: {
          energy: '111.8', carbohydrate: '22.9', protein: '2.25', fat: '1.39', fiber: '2.1'
        }
      },
      {
        id: 7, cat_id: 2, image: '/img/موسلی-سیب-و-دارچین.png',
        title: 'موسلی سیب و دارچین',
        subTitle: 'با سیب و دارچین',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی روی، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، سیب خشک، بادام، مویز، تخم کتان، مغز تخم آفتابگردان، دارچین',
        nutritional_value: {
          energy: '117.4', carbohydrate: '22', protein: '2.93', fat: '2.2', fiber: '2.17'
        }
      },
      {
        id: 8, cat_id: 2, image: '/img/موسلی-نارگیل-و-شکلات-تلخ.png',
        title: 'موسلی‌نارگیل و شکلات‌تلخ',
        subTitle: 'با نارگیل و شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آهن، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، نارگیل، شکلات تلخ، بادام، تخم کدو، دانه چیا',
        nutritional_value: {
          energy: '131.6', carbohydrate: '19.5', protein: '3.33', fat: '5.04', fiber: '2.6'
        }
      },
      {
        id: 9, cat_id: 2, image: '/img/موسلی-کرنبری.png',
        title: 'موسلی کرنبری',
        subTitle: 'با کرنبری',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آنتی‌اکسیدان و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، کرنبری، بادام، کشمش',
        nutritional_value: {
          energy: '113.8', carbohydrate: '23.1', protein: '2.6', fat: '1.4', fiber: '2'
        }
      },
      {
        id: 10, cat_id: 2, image: '/img/موسلی-کره-بادام-زمینی.png',
        title: 'موسلی کره بادام زمینی',
        subTitle: 'با کره بادام زمینی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، کره بادام زمینی، سویا، کینوآ، پروتئین تلغیظ شده آب پنیر، بادام زمینی، شکلات تلخ',
        nutritional_value: {
          energy: '122.6', carbohydrate: '17.7', protein: '6.2', fat: '3.3', fiber: '1.8'
        }
      },
      {
        id: 11, cat_id: 3, image: '/img/پروتیین-بار-فندق.png',
        title: 'پروتئین بار فندق',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه فندق، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {
        id: 12, cat_id: 3, image: '/img/پروتیین-بار-موزی.png',
        title: 'پروتئین بار موزی',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه موز، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {
        id: 13, cat_id: 3, image: '/img/پروتیین-بار-پرتغال.png',
        title: 'پروتئین بار پرتغال',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه پرتقالی، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {
        id: 14, cat_id: 3, image: '/img/پروتیین-بار-کارامل.png',
        title: 'پروتئین بار کارامل',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه کارامل، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },

    ];
    const product = ref({});
    const sameProducts = ref({});
    onMounted(() => {
      window.scrollTo({ top: 0, behavior: 'smooth' });
      product.value = pros.find((element) => element.id == route.params.id);
      sameProducts.value = pros.filter((element) => element.cat_id == product.value.cat_id &&  element.id != product.value.id);
    })

    return {
      product, pros, route,sameProducts
    }
  }

}
</script>

<style scoped>

</style>