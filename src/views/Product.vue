<template>
  <div id="header" class="">
    <the-nav-bar />
  </div>
  <main>
    <div class="w-100 main-bg row m-0 p-0 justify-content-center py-5">
      <div class="col-10 row m-0 p-0 justify-content-center justify-content-md-start">
        <div class="col-10 mb-5 mb-md-0 col-md-4 main-bg-light rounded">
          <lazy-image :data="product" />
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

   <div class="container-fluid">
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
           <div class="col-md-10 col-xl-7 d-none d-md-block text-center text-md-start">
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

     <div class="w-100  text-center  px-3 px-md-5  text-md-end">
       <strong class="px-3">محصولات مشابه</strong>
       <div id="same-products" class="w-100 p-0 m-0 row mt-3 justify-content-md-end">
         <a :href="'/product/'+pro.id" :key="pro.id" v-for="pro in random4" class="product-box-wrapper col-6 col-md-3 col-lg-2">
           <div class="product-box">
             <lazy-image :data="pro"/>
             <p class="product-title">{{ pro.title }}</p>
           </div>
         </a>
       </div>
     </div>
   </div>
  </main>
<the-footer />
</template>

<script>
import {onMounted, ref} from "vue";
import {useRoute} from "vue-router/dist/vue-router";
import TheNavBar from '@/components/TheNavBar.vue'
import TheFooter from '@/components/TheFooter.vue'
import LazyImage from '@/components/LazyImage.vue'


export default {
  name: "Product",
  components: {
    TheNavBar,TheFooter,LazyImage
  },
  setup() {

    const route = useRoute();

    const pros = [

      {id:1,cat_id: 1, image: '/img/انرژی‌بار بادام زمینی- ساشه.png', title: 'انرژی‌بار بادام زمینی',
        subTitle: 'با کره بادام زمینی و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 12% پروتئین',
        weight: 45,
        ingredients: 'جو پرک، جو دوسر پرک، عسل، کره بادام زمینی، غلات فرآوری شده گندم و ذرت، بادام زمینی، روغن کنجد، دارچین، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '197.1', carbohydrate: '28.12', protein: '5.53', fat: '7.87', fiber: '1'
        }
      },
      {id:2,cat_id: 1, image: '/img/انرژی‌بار دانه و کشمش- ساشه.png', title: 'انرژی‌بار دانه و کشمش',
        subTitle: 'با کشمش و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، خرما، عسل، کشمش، مغز تخم آفتابگردان، مغز تخم کدو، غلات فرآوری شده گندم و ذرت، طعم‌دهنده طبیعی مجاز خوراکی، روغن کنجد، روغن نارگیل',
        nutritional_value: {
          energy: '122.6', carbohydrate: '23.71', protein: '3.5', fat: '1.72', fiber: '1.96'
        }
      },

      {id:3,cat_id: 1, image: '/img/انرژی‌بار دانه چیا- ساشه.png', title: 'انرژی‌بار دانه چیا',
        subTitle: 'با دانه چیا و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، خرما، عسل، دانه چیا، غلات فرآوری شده گندم و ذرت، کنجد، فندق، مغز تخم آفتابگردان، روغن نارگیل، هل، زنجبیل، طعم‌دهنده مشابه طبیعی لیمو، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '130.83', carbohydrate: '22.85', protein: '3.46', fat: '3.19', fiber: '2.13'
        }
      },
      {id:4,cat_id: 1, image: '/img/انرژی‌بار نارگیل- ساشه.png', title: 'انرژی‌بار نارگیل',
        subTitle: 'با نارگیل و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 10% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دوسر پرک، عسل، پودر نارگیل، غلات فرآوری شده گندم و ذرت، مغز تخم آفتابگردان، کنجد، فندق، روغن نارگیل، روغن کنجد، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '147.14', carbohydrate: '21.24', protein: '3.29', fat: '6.14', fiber: '1.92'
        }
      },
      {id:5,cat_id: 1, image: '/img/انرژی‌بار کرنبری- ساشه.png', title: 'انرژی‌بار کرنبری',
        subTitle: 'با کرنبری و مغز دانه‌های خوراکی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 9% پروتئین',
        weight: 35,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، کرنبری، غلات فرآوری شده گندم و ذرت، خرما، بادام، ارده، روغن نارگیل، تمشک، نمک تصفیه شده خوراکی',
        nutritional_value: {
          energy: '137.9', carbohydrate: '26.4', protein: '3', fat: '2.5', fiber: '1'
        }
      },

      {id:6,cat_id: 1, image: '/img/انرژی‌بار لقمه بادام زمینی- ساشه.png', title: 'انرژی‌بار لقمه بادام زمینی', },
      {id:7,cat_id: 1, image: '/img/انرژی‌بار لقمه دانه و کشمش- ساشه.png', title: 'انرژی‌بار لقمه دانه و کشمش', },
      {id:8,cat_id: 1, image: '/img/انرژی‌بار لقمه دانه چیا- ساشه.png', title: 'انرژی‌بار لقمه دانه چیا', },
      {id:9,cat_id: 1, image: '/img/انرژی‌بار لقمه نارگیل- ساشه.png', title: 'انرژی‌بار لقمه نارگیل', },
      {id:10,cat_id: 1, image: '/img/انرژی‌بار لقمه کرنبری- ساشه.png', title: 'انرژی‌بار لقمه کرنبری', },

      {id:11,cat_id: 1, image: '/img/کیسه انرژی‌بار لقمه.png', title: 'انرژی‌بار لقمه بسته 15 عددی', },


      {id:12,cat_id: 4, image: '/img/فروت‌بار آلبالو- ساشه.png', title: 'فروت‌بار آلبالو', },
      {id:13,cat_id: 4, image: '/img/فروت‌بار انار- ساشه.png', title: 'فروت‌بار انار', },
      {id:14,cat_id: 4, image: '/img/فروت‌بار زردآلو- ساشه.png', title: 'فروت‌بار زردآلو', },
      {id:15,cat_id: 4, image: '/img/فروت‌بار موز و رزبری- ساشه.png', title: 'فروت‌بار موز و رزبری', },
      {id:16,cat_id: 4, image: '/img/فروت‌بار میکس بری- ساشه.png', title: 'فروت‌بار میکس بری', },
      {id:17,cat_id: 4, image: '/img/فروت‌بار هلو و انجیر- ساشه.png', title: 'فروت‌بار هلو و انجیر', },

      {id:18,cat_id: 4, image: '/img/باکس فروت‌بار آلبالو.png', title: 'باکس فروت‌بار آلبالو', },
      {id:19,cat_id: 4, image: '/img/باکس فروت‌بار انار.png', title: 'باکس فروت‌بار انار', },
      {id:20,cat_id: 4, image: '/img/باکس فروت‌بار زردآلو.png', title: 'باکس فروت‌بار زردآلو', },
      {id:21,cat_id: 4, image: '/img/باکس فروت‌بار موز و رزبری.png', title: 'باکس فروت‌بار موز و رزبری', },
      {id:22,cat_id: 4, image: '/img/باکس فروت‌بار میکس بری.png', title: 'باکس فروت‌بار میکس بری', },
      {id:23,cat_id: 4, image: '/img/باکس فروت‌بار هلو و انجیر.png', title: 'باکس فروت‌بار هلو و انجیر', },

      {id:24,cat_id: 2, image: '/img/پاوچ موسلی انار و پاپریکا.png', title: 'موسلی انار و پاپریکا', },
      {id:25,cat_id: 2, image: '/img/پاوچ موسلی بادام زمینی.png', title: 'موسلی بادام زمینی',
        subTitle: 'با کره بادام زمینی',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، کره بادام زمینی، سویا، کینوآ، پروتئین تلغیظ شده آب پنیر، بادام زمینی، شکلات تلخ',
        nutritional_value: {
          energy: '122.6', carbohydrate: '17.7', protein: '6.2', fat: '3.3', fiber: '1.8'
        }
      },
      {id:26,cat_id: 2, image: '/img/پاوچ موسلی زردآلو.png', title: 'موسلی زردآلو',
        subTitle: 'با زردآلو و کشمش',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آهن، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، زردآلو، فندق، کشمش',
        nutritional_value: {
          energy: '111.8', carbohydrate: '22.9', protein: '2.25', fat: '1.39', fiber: '2.1'
        }
      },
      {id:27,cat_id: 2, image: '/img/پاوچ موسلی سیب و دارچین.png', title: 'موسلی سیب و دارچین',
        subTitle: 'با سیب و دارچین',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی روی، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، سیب خشک، بادام، مویز، تخم کتان، مغز تخم آفتابگردان، دارچین',
        nutritional_value: {
          energy: '117.4', carbohydrate: '22', protein: '2.93', fat: '2.2', fiber: '2.17'
        }
      },
      {id:28,cat_id: 2, image: '/img/پاوچ موسلی نارگیل و شکلات تلخ.png', title: 'موسلی نارگیل و شکلات تلخ',
        subTitle: 'با نارگیل و شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آهن، منیزیم و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، جو دو سر پرک، عسل، نارگیل، شکلات تلخ، بادام، تخم کدو، دانه چیا',
        nutritional_value: {
          energy: '131.6', carbohydrate: '19.5', protein: '3.33', fat: '5.04', fiber: '2.6'
        }
      },
      {id:29,cat_id: 2, image: '/img/پاوچ موسلی پسته و گل محمدی.png', title: 'موسلی پسته و گل محمدی', },
      {id:30,cat_id: 2, image: '/img/پاوچ موسلی کرنبری.png', title: 'موسلی کرنبری',
        subTitle: 'با کرنبری',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی آنتی‌اکسیدان و فیبر طبیعی',
        weight: 350,
        ingredients: 'جو پرک، عسل، کرنبری، بادام، کشمش',
        nutritional_value: {
          energy: '113.8', carbohydrate: '23.1', protein: '2.6', fat: '1.4', fiber: '2'
        }
      },

      {id:31,cat_id: 2, image: '/img/موسلی باکس انار و پاپریکا.png', title: 'موسلی باکس انار و پاپریکا', },
      {id:32,cat_id: 2, image: '/img/موسلی باکس بادام زمینی.png', title: 'موسلی باکس بادام زمینی', },
      {id:33,cat_id: 2, image: '/img/موسلی باکس زردآلو.png', title: 'موسلی باکس زردآلو', },
      {id:34,cat_id: 2, image: '/img/موسلی باکس سیب و دارچین.png', title: 'موسلی باکس سیب و دارچین', },
      {id:35,cat_id: 2, image: '/img/موسلی باکس نارگیل و شکلات تلخ.png', title: 'موسلی باکس نارگیل و شکلات تلخ', },
      {id:36,cat_id: 2, image: '/img/موسلی باکس پسته و گل محمدی.png', title: 'موسلی باکس پسته و گل محمدی', },
      {id:37,cat_id: 2, image: '/img/موسلی باکس کرنبری.png', title: 'موسلی باکس کرنبری', },


      {id:38,cat_id: 3, image: '/img/پروتئین‌بار سوفیت فندق.png', title: 'پروتئین‌بار سوفیت فندق',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه فندق، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {id:39,cat_id: 3, image: '/img/پروتئین‌بار سوفیت قهوه.png', title: 'پروتئین‌بار سوفیت قهوه', },
      {id:40,cat_id: 3, image: '/img/پروتئین‌بار سوفیت موز.png', title: 'پروتئین‌بار سوفیت موز',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه موز، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {id:41,cat_id: 3, image: '/img/پروتئین‌بار سوفیت پرتقال.png', title: 'پروتئین‌بار سوفیت پرتقال',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه پرتقالی، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {id:42,cat_id: 3, image: '/img/پروتئین‌بار سوفیت کارامل.png', title: 'پروتئین‌بار سوفیت کارامل',
        subTitle: 'با روکش شکلات تلخ',
        sugar: 'بدون شکر افزوده، فقط با عسل طبیعی',
        contains: 'حاوی 30% پروتیئن وی',
        weight: 45,
        ingredients: 'مجموعه پروتئینی (پروتئین ایزوله سویا، پروتئین تلغیظ شده شیر، دانه سویا، پروتئین تلغیظ شده آب پنیر، شاه دانه)، عسل، روغن کنجد، کره بادام درختی، فرآورده حجیم شده گندم، پودر کاکائو، لسیتین سویا، نمک تصفیه شده خوراکی، طعم دهنده مشابه کارامل، زانتان، آب، فرآوره کاکائویی تلخ',
        nutritional_value: {
          energy: '151.65', carbohydrate: '13.60', protein: '13.83', fat: '4.3', fiber: '2.25'
        }
      },
      {id:43,cat_id: 3, image: '/img/پروتئین‌بار لقمه سوفیت فندق.png', title: 'پروتئین‌بار لقمه سوفیت فندق', },
      {id:44,cat_id: 3, image: '/img/پروتئین‌بار لقمه سوفیت قهوه.png', title: 'پروتئین‌بار لقمه سوفیت قهوه', },
      {id:45,cat_id: 3, image: '/img/پروتئین‌بار لقمه سوفیت موز.png', title: 'پروتئین‌بار لقمه سوفیت موز', },
      {id:46,cat_id: 3, image: '/img/پروتئین‌بار لقمه سوفیت پرتقال.png', title: 'پروتئین‌بار لقمه سوفیت پرتقال', },
      {id:47,cat_id: 3, image: '/img/پروتئین‌بار لقمه سوفیت کارامل.png', title: 'پروتئین‌بار لقمه سوفیت کارامل', },
      {id:48,cat_id: 3, image: '/img/کیسه پروتئین‌بار سوفیت لقمه.png', title: 'پروتئین‌بار لقمه سوفیت بسته 12 عددی', },

      {id:49,cat_id: 5, image: '/img/پروتئین‌بار زیرو سوفیت- بادام زمینی ساشه.png', title: 'پروتئین‌بار زیرو سوفیت بادام زمینی', },
      {id:50,cat_id: 5, image: '/img/پروتئین‌بار زیرو سوفیت- براونی ساشه.png', title: 'پروتئین‌بار زیرو سوفیت براونی', },
      {id:51,cat_id: 5, image: '/img/پروتئین‌بار زیرو سوفیت- سیب و دارچین ساشه.png', title: 'پروتئین‌بار زیرو سوفیت سیب و دارچین', },
      {id:52,cat_id: 5, image: '/img/پروتئین‌بار زیرو سوفیت- موز و توت‌فرنگی ساشه.png', title: 'پروتئین‌بار زیرو سوفیت موز و توت‌فرنگی', },
      {id:53,cat_id: 5, image: '/img/پروتئین‌بار زیرو سوفیت- کارامل نمکی ساشه.png', title: 'پروتئین‌بار زیرو سوفیت کارامل نمکی', },

      {id:54,cat_id: 5, image: '/img/باکس پروتئین‌بار زیرو سوفیت- بادام زمینی.png', title: 'پروتئین‌بار زیرو سوفیت بادام زمینی', },
      {id:55,cat_id: 5, image: '/img/باکس پروتئین‌بار زیرو سوفیت- براونی.png', title: 'پروتئین‌بار زیرو سوفیت براونی', },
      {id:56,cat_id: 5, image: '/img/باکس پروتئین‌بار زیرو سوفیت- سیب و دارچین.png', title: 'پروتئین‌بار زیرو سوفیت سیب و دارچین', },
      {id:57,cat_id: 5, image: '/img/باکس پروتئین‌بار زیرو سوفیت موز و توت‌فرنگی.png', title: 'پروتئین‌بار زیرو سوفیت موز و توت‌فرنگی', },
      {id:58,cat_id: 5, image: '/img/باکس پروتئین‌بار زیرو سوفیت- کارامل نمکی.png', title: 'پروتئین‌بار زیرو سوفیت کارامل نمکی', },

    ];
    const product = ref({});
    const sameProducts = ref({});
    const shuffled = ref([]);
    const random4 = ref([]);
    onMounted(() => {
      window.scrollTo({ top: 0, behavior: 'smooth' });
      product.value = pros.find((element) => element.id == route.params.id);
      sameProducts.value = pros.filter((element) => element.cat_id == product.value.cat_id &&  element.id != product.value.id);

      const random = [];

      while (random.length < 4) {
        const index = Math.floor(Math.random() * sameProducts.value.length);

        if (!random.includes(sameProducts.value[index])) {
          random.push(sameProducts.value[index]);
        }
        }
      random4.value = random;
    })

    return {
      product, pros, route,sameProducts,random4,shuffled
    }
  }

}
</script>

<style scoped>

</style>