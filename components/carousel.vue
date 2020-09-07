<template>
  <div id="carouselExampleControls" class="carousel slide" data-ride="carousel">
    <div class="carousel-inner">
      <div class="carousel-item active bg-gray">
        <div class="text-center my-3">
          <img src="@/assets/images/carousel1.png" alt="" />
        </div>
      </div>
      <div class="carousel-item bg-gray">
        <div class="text-center my-3 position-relative">
          <img class="" src="@/assets/images/carousel2fix.png" alt="" />
          <nuxt-link to="/post">
            <button
              class="position-absolute btn-absolute btn btn-success px-5 d-lg-block d-xl-block d-sm-none d-md-none d-xs-none"
            >
              สร้าง
            </button>
          </nuxt-link>
        </div>
      </div>
      <div class="carousel-item bg-gray">
        <div class="text-center my-3">
          <img class src="@/assets/images/carousel3.png" alt />
        </div>
      </div>
    </div>
    <a
      class="carousel-control-prev"
      href="#carouselExampleControls"
      role="button"
      data-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a
      class="carousel-control-next"
      href="#carouselExampleControls"
      role="button"
      data-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</template>

<script>
export default {}
</script>

<style lang="css" scoped>
.btn-absolute {
  bottom: 20%;
  right: 34%;
}
</style>
