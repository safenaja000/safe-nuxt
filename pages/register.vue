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
        <v-btn
          style="background-color: #f7f7f7; outline: none; border: none;"
          class="d-inline-block rounded-pill px-3 m-3 p-2"
          @click="setUser()"
          >กดเพื่อส่งข้อมูล</v-btn
        >
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2'
export default {
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
  methods: {
    async setUser() {
      if (this.password !== this.confirmpassworn) {
        Swal.fire({
          icon: 'error',
          title: 'Oops...',
          text: 'Password not Equal',
        })
      } else {
        const res = await this.$axios.$post('/member', {
          id_card: this.id_card,
          name: this.name,
          email_address: this.email_address,
          phone_no: this.phone_no,
          member_type: this.member_type,
          username: this.username,
          password: this.password,
        })
        if (res.status !== 'OK') {
          Swal.fire({
            icon: 'error',
            title: 'สมัครสมาชิกไม่สำเร็จ',
            text: 'กระรุณาตรวจสอบข้อมูลของท่าน',
          })
        } else {
          this.$router.replace({ path: '/login' })
        }
      }
    },
  },
}
</script>

<style></style>
