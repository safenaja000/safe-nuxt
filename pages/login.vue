<template>
  <div class="container my-5">
    <!-- style="background-image: url(./backgroud.jpg); border: 1px solid #E9E6E6; opacity: 0.15;"-->
    <div class="row">
      <div class="col-lg-12" style="background-color: #fefcf8;">
        <div class="row my-5">
          <div class="col-lg-12 text-right">
            <h3
              style="background-color: #f7f7f7;"
              class="d-inline-block rounded m-3 p-2"
            >
              ร่วมแสดงความคิดเห็น เข้าชื่อเสนอร่างกฏหมาย
            </h3>
          </div>
          <div class="col-lg-8 ml-auto">
            <div class="form-group">
              <label for>Username</label>
              <input
                class="form-control"
                type="text"
                name="username"
                id
                placeholder="/* กรุณากรอก Username */"
              />
            </div>
            <div class="form-group">
              <label for>Password</label>
              <input
                class="form-control"
                type="text"
                name="password"
                id
                placeholder="/* กรุณากรอก Password */"
              />
            </div>
            <div class="form-group">
              <button class="d-inline-block btn btn-danger">เข้าสู่ระบบ</button>
              <nuxt-link class="bg-gray btn" to="/register"
                >สมัครสมาชิก</nuxt-link
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
