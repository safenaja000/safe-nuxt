<template>
  <div>
    <nav class="navbar navbar-light bg-gray">
      <a class="navbar-brand" href="#">
        <img class="pt-2" width="50px" src="@/assets/images/logo.png" alt />
      </a>
      <a class="navbar-brand mr-auto" href="#">
        <p>
          <b>รัฐสภาไทย</b>
          The National Assembly
        </p>
      </a>
      <!--
      <a class="navbar-brand" href="#">
        <img class="pt-2" width="30px" src="@/assets/images/logo3.png" alt />
      </a>
      <a class="navbar-brand mr-sm-auto" href="#">
        <div class="text-left">
          <img class="pt-2" width="50px" src="@/assets/images/logo2.png" alt />
        </div>
      </a>-->
      <!-- <nuxt-link v-if="checklocation == 'http://localhost:3000/register'"
        class="navbar-brand ml-sm-auto d-none d-sm-none d-md-block d-lg-block"
        to="/login"
      >
        <div class="text-right">
          <button class="btn rounded-pill btn-danger bg-dangerdark px-5">
            Login
          </button>
        </div>
      </nuxt-link>-->
      <p>ยินดีต้อนรับ คุณวรรธนัย สาธุพันธ์</p>
      <div class="mx-auto d-md-none d-lg-none d-sm-block">
        <nuxt-link to="/login">
          <button class="btn rounded-pill btn-danger bg-dangerdark px-5">Login</button>
        </nuxt-link>
      </div>
    </nav>

    <div class="container-fluid m-0 p-0">
      <div class="row bg-dangerdark p-3">
        <div class="col-lg-12">
          <div class="row">
            <nuxt-link
              class="nav-link text-white col-12 col-lg-1 text-center hvr-sweep-to-right"
              to="/"
            >หน้าแรก</nuxt-link>
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              to="/post"
            >ร้องขอจัดทำร่างกฏหมาย</nuxt-link>
            <nuxt-link
              to="/searchPost"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
            >ตรวจสอบสถานะ</nuxt-link>
            <nuxt-link
              class="nav-link text-white col-12 col-lg-1 text-center hvr-sweep-to-right"
              href
              to="/addpost"
            >เริ่มร่างกฏหมาย</nuxt-link>
            <nuxt-link
              to="/lawknowledge"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
            >ข่าวสารและสาระน่ารู้</nuxt-link>
            <nuxt-link
              to="/mylaws"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
            >ร่างกฏหมายของท่าน</nuxt-link>
            <nuxt-link
              to="/question"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
            >คำถามที่พบบ่อย</nuxt-link>
          </div>
        </div>
      </div>
    </div>
    <Nuxt />
    <i
      class="fas fa-comment-dots position-fixed"
      style="font-size: 5rem; right: 0; bottom: 0; color: #33fffc;"
    ></i>
    <div class="container-fluid bg-dangerdark">
      <div class="row text-right ml-auto py-2">
        <div class="col-lg-11"></div>
        <div class="col-lg-1">
          <a class="text-right pr-2" href>
            <i class="fab fa-facebook-square text-primary" style="font-size: 2rem;"></i>
          </a>
          <a class="text-right pr-2" href>
            <i class="fab fa-line text-success" style="font-size: 2rem;"></i>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
