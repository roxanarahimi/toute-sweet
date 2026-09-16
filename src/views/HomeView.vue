<template>
  <div id="header" class="">
    <the-nav-bar />
    <div class="w-100 px-lg-5" style="background-color: #1A453C">
      <img src="/img/banner.png" class="px-lg-5" width="100%" alt="">
    </div>
  </div>

  <main class="container-fluid">

    <div id="categories" class="w-100 d-flex flex-wrap justify-content-center justify-content-md-center pt-5 mb-5">
      <div v-for="cat in categories" class="cat-box-wrapper mx-2 mx-md-3 my-3 my-lg-0 ">
        <div class="cat-box p-3" @click="filterProducts(cat.id)">
          <lazy-image :data="cat"/>
          <p class="cat-title">{{ cat.title }}</p>
        </div>
      </div>
    </div>

    <div id="products" class=" w-100 p-0 m-0 mt-5 px-0 px-md-5 row">
      <a :href="'/product/'+pro.id" v-for="(pro,index) in products" :key="pro.id" class="product-box-wrapper h-100" :class="{'col-6 col-lg-2':!catFilter&&!more,'col-12 col-lg-2':catFilter&&more, 'col-12 col-lg-4':catFilter&&!more}">
        <div class="product-box">
          <lazy-image :data="pro" :index="pro.id" />
          <p class="product-title">{{ pro.title }}</p>
        </div>
      </a>
     <div v-if="catFilter" class="text-center">
       <button v-if="!more" @click="wantMore(catFilter)" class="btn btn-dark mb-5 mx-auto text-light" >نمایش همه</button>
     </div>
    </div>


  </main>
  <the-footer />
</template>

<script>
// @ is an alias to /src
import TheNavBar from '@/components/TheNavBar.vue'
import TheFooter from '@/components/TheFooter.vue'
import LazyImage from '@/components/LazyImage.vue'
import {onMounted, ref} from "vue";
import App from "@/App.vue";

export default {
  name: 'HomeView',
  components: {
    TheNavBar,TheFooter,LazyImage
  },
  setup() {

    const pros0 = [

    ];
    const categories = App.setup().categories;
    const pros = App.setup().pros;
    const products = ref([]);
    const catFilter = ref(0);
    const more = ref(false);
    onMounted(() => {
      catFilter.value = 0;
      products.value = pros0;
      if (localStorage.getItem('scroll')){
        document.querySelector('#'+localStorage.getItem('scroll'))?.scrollIntoView();
      }else{
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
      localStorage.removeItem('scroll')

      // preload();
    });
    const filterProducts = (id) => {
      more.value = false;
      catFilter.value = id;
      document.querySelectorAll('.cat-box').forEach((element)=>{
        element.style.width='140px';
        element.style.height='140px';
        element.style.fontSize='12px';
      })
      document.querySelectorAll('.product-box').forEach((element)=>{
        element.classList.add('zoomOut');
      })

          setTimeout(()=>{
            products.value = [];
            products.value = pros.filter((element) => {
              return element.cat_id === id;
            }).splice(0,3)
            document.querySelectorAll('.product-box').forEach((element)=>{
              element.classList.remove('zoomOut');
              element.classList.add('zoomIn');
            })
            document.querySelector('#products')?.scrollIntoView();

          },600)
    }

    const wantMore = (id)=>{
      more.value = true
      document.querySelectorAll('.product-box').forEach((element)=>{
        element.classList.add('zoomOut');
      })

      setTimeout(()=>{
        products.value = [];
        products.value = pros.filter((element) => {
          return element.cat_id === id;
        })
        document.querySelectorAll('.product-box').forEach((element)=>{
          element.classList.remove('zoomOut');
          element.classList.add('zoomIn');
        })
      },600)
    }
    const preload = () => {
        pros.forEach(p => {
          const img = new Image();
          img.src = p.image;
        });
    }

    return {
      products, categories, pros0, pros, filterProducts,
      catFilter, preload,scroll,more,wantMore
    }
  }
}
</script>
