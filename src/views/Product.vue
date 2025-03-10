<template>
  <div id="header" class="">
    <the-nav-bar />
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
<the-footer />
</template>

<script>
import {onMounted, ref} from "vue";
import {useRoute} from "vue-router/dist/vue-router";
import TheNavBar from '@/components/TheNavBar.vue'
import TheFooter from '@/components/TheFooter.vue'


export default {
  name: "Product",
  components: {
    TheNavBar,TheFooter,
  },
  setup() {

    const route = useRoute();

    const pros = [
      {
        id: 1, cat_id: 1, image: '/img/گرانولابار دانه و کشمش.png',
        title: 'انرژی‌بار دانه و کشمش',
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
        title: 'انرژی‌بار دانه چیا',
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
        title: 'انرژی‌بار بادام زمینی',
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
        title: 'انرژی‌بار نارگیل',
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
        title: 'انرژی‌بار کرنبری',
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