<template>
  <nav class="navbar navbar-expand-lg">
    <div class="container-fluid d-flex justify-content-between">
      <div class="d-none d-lg-block">
        <router-link to="/" class="navbar-brand cursor"><img src="/img/logoW.png" width="100px" alt=""></router-link>
      </div>
      <div class="navbar-toggler text-light border-0 cursor"  data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown"
           aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" fill="currentColor" class="bi bi-list" viewBox="0 0 16 16">
          <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5m0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5m0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5"/>
        </svg>
      </div>
      <div class="d-lg-none">
        <router-link to="/" class="navbar-brand cursor"><img src="/img/logoW.png" width="70px" alt=""></router-link>
      </div>
      <div class="collapse navbar-collapse justify-content-center nvStyle" id="navbarNavDropdown" >
        <ul class="navbar-nav text-center">
          <li class="nav-item px-3">
            <router-link id="homeSection" to="/" class="nav-link cursor" aria-current="page">خانه</router-link>
          </li>
          <li class="nav-item px-3 cursor">
            <a id="categoriesSection" class="nav-link" @click="scrollTo('categories')">محصولات</a>
          </li>
<!--          <li class="nav-item px-3">-->
<!--            <a id="footerSection" class="nav-link" @click="scrollTo('footer')">درباره ما</a>-->
<!--          </li>-->
          <li class="nav-item px-3 cursor">
            <a id="footerSection" class="nav-link" @click="scrollTo('footer')">تماس با ما</a>
          </li>
        </ul>
      </div>

      <div class="d-none d-lg-block">
        <a class="navbar-brand" href="#"><i class="bi bi-search"></i></a>
      </div>
    </div>
  </nav>
</template>

<script>
import App from '../App.vue'

export default {
  name: "TheNavBar",
  components:{App},
  setup(){
    const scrollTo = (id)=>{
      if(window.innerWidth<992){
        document.querySelector('.navbar-toggler').click();
      }
      document.querySelector('#'+id)?.scrollIntoView();
    }
    return{
      scrollTo,
    }
  }

}
</script>

<style scoped>

</style>