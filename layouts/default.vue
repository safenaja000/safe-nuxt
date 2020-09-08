<template>
  <div>
    <nav class="navbar navbar-light bg-gray">
      <a class="navbar-brand" href="#">
        <img class="pt-2" width="50px" src="@/assets/images/logo.png" alt />
      </a>
      <a class="navbar-brand" href="#">
        <img class width="50px" src="@/assets/images/logo4.png" alt />
      </a>
      <a class="navbar-brand" href="#">
        <img class="pt-2" width="50px" src="@/assets/images/logo3.png" alt />
      </a>
      <a class="navbar-brand mr-sm-auto" href="#">
        <div class="text-left">
          <img class="pt-2" width="50px" src="@/assets/images/logo2.png" alt />
        </div>
      </a>
      <nuxt-link
        class="navbar-brand ml-sm-auto d-none d-sm-none d-md-block d-lg-block"
        to="/login"
      >
        <div class="text-right">
          <button class="btn rounded-pill btn-danger bg-dangerdark px-5">
            Login
          </button>
        </div>
      </nuxt-link>
      <div class="mx-auto d-md-none d-lg-none d-sm-block">
        <nuxt-link to="/login">
          <button class="btn rounded-pill btn-danger bg-dangerdark px-5">
            Login
          </button>
        </nuxt-link>
      </div>
    </nav>

    <div class="container-fluid m-0 p-0">
      <div class="row bg-dangerdark p-3">
        <div class="col-lg-12">
          <div class="row">
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              to="/"
            >
              หน้าแรก
            </nuxt-link>
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              to="/post"
            >
              ผู้ริเริ่มเสนอกฏหมาย
            </nuxt-link>
            <nuxt-link
              to="/searchPost"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
              >ตรวจสอบสถานะ</nuxt-link
            >
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
              to="/lawpass"
              >ร่างกฏหมายที่ผ่านตามขั้นตอน</nuxt-link
            >
            <nuxt-link
              to="/lawknowledge"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
              >ข่าวสารและสาระน่ารู้</nuxt-link
            >
            <nuxt-link
              to="/mylaws"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
              >ร่างกฏหมายของท่าน</nuxt-link
            >
          </div>
        </div>
      </div>
    </div>
    <Nuxt />
    <div class="container-fluid bg-dangerdark">
      <div class="row text-right ml-auto py-2">
        <div class="col-lg-11"></div>
        <div class="col-lg-1">
          <a class="text-right pr-2" href>
            <i
              class="fab fa-facebook-square text-primary"
              style="font-size: 2rem;"
            ></i>
          </a>
          <a class="text-right pr-2" href>
            <i class="fab fa-line text-success" style="font-size: 2rem;"></i>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
