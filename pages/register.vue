<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-lg-12" style="background: #fefcf8;">
        <div class="row">
          <div class="col-lg-12 text-right">
            <h3
              style="background-color: #f7f7f7;"
              class="d-inline-block rounded m-3 p-2"
            >
              ร่วมแสดงความคิดเห็น เข้าชื่อเสนอร่างกฏหมาย
            </h3>
          </div>
          <div class="col-lg-12">
            <div class="form-group">
              <div class="text-center">
                <img
                  class="text-center"
                  src="@/assets/images/user.png"
                  width="250"
                  alt
                />
              </div>
            </div>
            <div class="form-group">
              <label for>ชื่อ - นามสกุล :</label>
              <input
                class="form-control"
                type="text"
                name
                id
                placeholder="/* กรุณากรอกชื่อ - นามสกุล */"
              />
            </div>
            <div class="form-group">
              <label for>รหัสบัตรประชาชน :</label>
              <input
                class="form-control"
                type="text"
                name
                id
                placeholder="/* กรุณากรอกรหัสบัตรประชาชน */"
                minlength="13"
                maxlength="13"
              />
            </div>
            <div class="form-group">
              <label for>รหัสผ่าน :</label>
              <input
                class="form-control"
                type="password"
                name
                id
                placeholder="/* รหัสผ่าน */"
              />
            </div>
            <div class="form-group">
              <label for>ยืนยันรหัสผ่าน :</label>
              <input
                class="form-control"
                type="password"
                name
                id
                placeholder="/* ยืนยันรหัสผ่าน */"
              />
            </div>
            <div class="form-group">
              <label for>อีเมล :</label>
              <input
                class="form-control"
                type="email"
                name
                id
                placeholder="/* อีเมลของคุณ */"
              />
            </div>
            <div class="form-group">
              <label for>เบอร์โทร :</label>
              <input
                class="form-control"
                type="text"
                name
                id
                placeholder="/* กรุณากรอกเบอร์โทรศัพท์ */"
                minlength="10"
                maxlength="10"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="col-lg-12 text-right">
        <button
          style="background-color: #f7f7f7; outline: none; border: none;"
          class="d-inline-block rounded-pill px-3 m-3 p-2"
        >
          กดเพื่อส่งข้อมูล
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
