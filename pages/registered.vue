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
          <button class="btn rounded-pill btn-danger bg-dangerdark px-5">Login</button>
        </div>
      </nuxt-link>
      <!-- <p>ยินดีต้อน คุณ ปาริดา หงพรทิพ</p> -->
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
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              to="/"
            >หน้าแรก</nuxt-link>
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              to="/post"
            >ผู้ริเริ่มเสนอกฏหมาย</nuxt-link>
            <nuxt-link
              to="/searchPost"
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
              href
            >ตรวจสอบสถานะ</nuxt-link>
            <nuxt-link
              class="nav-link text-white col-12 col-lg-2 text-center hvr-sweep-to-right"
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
          </div>
        </div>
      </div>
    </div>
    <div class="container mt-5">
      <div class="row">
        <div class="col-lg-12" style="background: #fefcf8;">
          <div class="row">
            <div class="col-lg-12 text-right">
              <h3
                style="background-color: #f7f7f7;"
                class="d-inline-block rounded m-3 p-2"
              >ร่วมแสดงความคิดเห็น เข้าชื่อเสนอร่างกฏหมาย</h3>
            </div>
            <div class="col-lg-12">
              <!-- <div class="form-group">
              <div class="text-center">
                <img
                  class="text-center"
                  src="@/assets/images/user.png"
                  width="250"
                  alt
                />
              </div>
              </div>-->
              <div class="form-group">
                <label for>ชื่อ - นามสกุล :</label>
                <input
                  class="form-control"
                  type="text"
                  id
                  name
                  v-model="name"
                  placeholder="/* กรุณากรอกชื่อ - นามสกุล */"
                />
              </div>
              <div class="form-group">
                <label for>ชื่อผู้ใช้ :</label>
                <input
                  class="form-control"
                  type="text"
                  id
                  name
                  v-model="username"
                  placeholder="/* ชื่อผู้ใช้ */"
                />
              </div>
              <div class="form-group">
                <label for>รหัสบัตรประชาชน :</label>
                <input
                  class="form-control"
                  type="text"
                  id
                  name
                  placeholder="/* กรุณากรอกรหัสบัตรประชาชน */"
                  minlength="13"
                  maxlength="13"
                  v-model="id_card"
                />
              </div>
              <div class="form-group">
                <label for>รหัสผ่าน :</label>
                <input
                  class="form-control"
                  type="password"
                  id
                  name
                  placeholder="/* รหัสผ่าน */"
                  v-model="password"
                />
              </div>
              <div class="form-group">
                <label for>ยืนยันรหัสผ่าน :</label>
                <input
                  class="form-control"
                  type="password"
                  id
                  name
                  placeholder="/* ยืนยันรหัสผ่าน */"
                  v-model="confirmpassworn"
                />
              </div>
              <div class="form-group">
                <label for>อีเมล :</label>
                <input
                  class="form-control"
                  type="email"
                  id
                  name
                  placeholder="/* อีเมลของคุณ */"
                  v-model="email_address"
                />
              </div>
              <div class="form-group">
                <label for>เบอร์โทร :</label>
                <input
                  class="form-control"
                  type="text"
                  id
                  name
                  placeholder="/* กรุณากรอกเบอร์โทรศัพท์ */"
                  minlength="10"
                  maxlength="10"
                  v-model="phone_no"
                />
              </div>
            </div>
          </div>
        </div>
        <div class="col-lg-12 text-right">
          <v-btn to="/registercomfirm"
            style="background-color: #f7f7f7; outline: none; border: none;"
            class="d-inline-block rounded-pill px-3 m-3 p-2"
          >ขั้นตอนต่อไป</v-btn>
        </div>
      </div>
    </div>
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

<script>
import Swal from 'sweetalert2'
export default {
  layout: 'empty',
  data() {
    return {
      id_card: '',
      name: '',
      email_address: '',
      phone_no: '',
      member_type: 1,
      username: '',
      password: '',
      confirmpassworn: '',
    }
  },
}
</script>

<style>
</style>
