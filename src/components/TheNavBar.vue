<template>
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
</template>

<script>
export default {
  name: "TheNavBar"
}
</script>

<style scoped>

</style>