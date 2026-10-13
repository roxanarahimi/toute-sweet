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
               <tr v-if="product.nutritional_value?.energy"><th scope="col" class="ps-3">انرژی</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.energy }} Kcal</td></tr>
               <tr v-if="product.nutritional_value?.protein"><th scope="col" class="ps-3">پروتئین</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.protein }} g</td></tr>
               <tr v-if="product.nutritional_value?.carbohydrate"><th scope="col" class="ps-3">کربوهیدرات</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.carbohydrate}} g</td></tr>
               <tr v-if="product.nutritional_value?.Calcium"><th scope="col" class="ps-3">کلسیم</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.Calcium}} g</td></tr>
               <tr v-if="product.nutritional_value?.sugar"><th scope="col" class="ps-3">قند</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.sugar}} g</td></tr>
               <tr v-if="product.nutritional_value?.addedSugar"><th scope="col" class="ps-3">قند افزوده</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.addedSugar}} g</td></tr>
               <tr v-if="product.nutritional_value?.salt"><th scope="col" class="ps-3">نمک</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.salt}} g</td></tr>
               <tr v-if="product.nutritional_value?.sodium"><th scope="col" class="ps-3">سدیم</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.sodium}} g</td></tr>
               <tr v-if="product.nutritional_value?.cholesterol"><th scope="col" class="ps-3">کلسترول</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.cholesterol}} g</td></tr>
               <tr v-if="product.nutritional_value?.transFattyAcids"><th scope="col" class="ps-3">اسیدهای چرب ترانس</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.transFattyAcids}} g</td></tr>
               <tr v-if="product.nutritional_value?.saturatedFattyAcids"><th scope="col" class="ps-3">اسید های چرب اشباع</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.saturatedFattyAcids}} g</td></tr>
               <tr v-if="product.nutritional_value?.fat"><th scope="col" class="ps-3">چربی</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.fat}} g</td></tr>
               <tr v-if="product.nutritional_value?.fiber"><th scope="col" class="ps-3">فیبر</th><td dir="ltr" class="text-left pe-3">{{ product.nutritional_value?.fiber}} g</td></tr>
               </tbody>
             </table>
           </div>
           <div class="col-md-10 col-xl-9 d-none d-md-block text-center text-md-start">
             <div class="w-100 mt-5 px-3 px-md-5 mb-5">
               <strong>جدول ارزش غذایی {{ product.title }} در {{ product.weight }} گرم</strong>
               <table class="table table-responsive border text-center mt-3 w-100">
                 <thead>
                 <tr>
                   <th v-if="product.nutritional_value?.energy" scope="col">انرژی</th>
                   <th v-if="product.nutritional_value?.protein" scope="col">پروتئین</th>
                   <th v-if="product.nutritional_value?.carbohydrate" scope="col">کربوهیدرات</th>
                   <th v-if="product.nutritional_value?.Calcium" scope="col">کلسیم</th>
                   <th v-if="product.nutritional_value?.sugar" scope="col">قند</th>
                   <th v-if="product.nutritional_value?.addedSugar" scope="col">قند افزوده</th>
                   <th v-if="product.nutritional_value?.salt" scope="col">نمک</th>
                   <th v-if="product.nutritional_value?.sodium" scope="col">سدیم</th>
                   <th v-if="product.nutritional_value?.cholesterol" scope="col">کلسترول</th>
                   <th v-if="product.nutritional_value?.transFattyAcids" scope="col">اسیدهای چرب ترانس</th>
                   <th v-if="product.nutritional_value?.saturatedFattyAcids" scope="col">اسید های چرب اشباع</th>
                   <th v-if="product.nutritional_value?.fat" scope="col">چربی</th>
                   <th v-if="product.nutritional_value?.fiber" scope="col">فیبر</th>
                     </tr>
                 </thead>
                 <tbody>
                 <tr>
                   <td v-if="product.nutritional_value?.energy" dir="ltr">{{ product.nutritional_value?.energy }} Kcal</td>
                   <td v-if="product.nutritional_value?.protein" dir="ltr">{{ product.nutritional_value?.protein }} g</td>
                   <td v-if="product.nutritional_value?.carbohydrate" dir="ltr">{{ product.nutritional_value?.carbohydrate}} g</td>
                   <td v-if="product.nutritional_value?.Calcium" dir="ltr">{{ product.nutritional_value?.Calcium }} Kcal</td>
                   <td v-if="product.nutritional_value?.sugar" dir="ltr">{{ product.nutritional_value?.sugar }} g</td>
                   <td v-if="product.nutritional_value?.addedSugar" dir="ltr">{{ product.nutritional_value?.addedSugar }} g</td>
                   <td v-if="product.nutritional_value?.salt" dir="ltr">{{ product.nutritional_value?.salt }} g</td>
                   <td v-if="product.nutritional_value?.sodium" dir="ltr">{{ product.nutritional_value?.sodium}} g</td>
                   <td v-if="product.nutritional_value?.cholesterol" dir="ltr">{{ product.nutritional_value?.cholesterol}} g</td>
                   <td v-if="product.nutritional_value?.transFattyAcids" dir="ltr">{{ product.nutritional_value?.transFattyAcids}} g</td>
                   <td v-if="product.nutritional_value?.saturatedFattyAcids" dir="ltr">{{ product.nutritional_value?.saturatedFattyAcids}} g</td>
                   <td v-if="product.nutritional_value?.fat" dir="ltr">{{ product.nutritional_value?.fat}} g</td>
                   <td v-if="product.nutritional_value?.fiber" dir="ltr">{{ product.nutritional_value?.fiber}} g</td>

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