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
import App from "@/App.vue";


export default {
  name: "Product",
  components: {
    TheNavBar,TheFooter,LazyImage
  },
  setup() {

    const route = useRoute();

    const pros = App.setup().pros;
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