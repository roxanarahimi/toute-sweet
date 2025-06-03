<template>
  <div id="header" class="">
    <the-nav-bar />
    <div class="w-100">
      <img src="img/banner.jpg" width="100%" alt="">
    </div>
  </div>

  <main class="container-fluid">

    <div id="categories" class="w-100 d-flex justify-content-between justify-content-md-center py-5 mb-5">
      <div v-for="cat in categories" class="cat-box-wrapper mx-md-3">
        <div class="cat-box" @click="filterProducts(cat.id)">
          <lazy-image :data="cat"/>
          <p class="cat-title">{{ cat.title }}</p>
        </div>
      </div>
    </div>

    <div id="products" class="w-100 p-0 m-0 px-0 px-md-5 row">
      <router-link :to="'/product/'+pro.id" v-for="pro in products" :key="pro.id" class="product-box-wrapper h-100" :class="{'col-12 col-lg-4':catFilter, 'col-6 col-lg-2':!catFilter}">
        <div class="product-box h-100">
          <lazy-image :data="pro" :index="pro.id" />
          <p class="product-title">{{ pro.title }}</p>
        </div>
      </router-link>
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

export default {
  name: 'HomeView',
  components: {
    TheNavBar,TheFooter,LazyImage
  },
  setup() {
    const categories = [
      {id: 1, image: '/img/گرانولابار-نارگیل.png', title: 'انرژی بار'},
      {id: 2, image: '/img/موسلی-نارگیل-و-شکلات-تلخ.png', title: 'موسلی'},
      {id: 3, image: '/img/پروتیین-بار-فندق.png', title: 'پروتئین بار سوفیت'},
    ];
    const pros = [
      {id:1,cat_id: 1, image: '/img/گرانولابار دانه و کشمش.png', title: 'انرژی‌بار دانه و کشمش', text: ''},
      {id:2,cat_id: 1, image: '/img/گرانولابار دانه-چیا.png', title: 'انرژی‌بار دانه چیا', text: ''},
      {id:3,cat_id: 1, image: '/img/گرانولابار-بادام-زمینی.png', title: 'انرژی‌بار بادام زمینی', text: ''},
      {id:4,cat_id: 1, image: '/img/گرانولابار-نارگیل.png', title: 'انرژی‌بار نارگیل', text: ''},
      {id:5,cat_id: 1, image: '/img/گرانولابار-کرنبری.png', title: 'انرژی‌بار کرنبری', text: ''},
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
      products.value = pros;
      window.scrollTo({ top: 0, behavior: 'smooth' });
      // preload();
    });
    const filterProducts = (id) => {
      catFilter.value = true;
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
      products, categories, pros, filterProducts, catFilter, preload,scroll
    }
  }
}
</script>
