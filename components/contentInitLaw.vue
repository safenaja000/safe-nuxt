<template>
  <div
    v-if="post != null"
    class="col-lg-12 rounded"
    style="background-color: #ffffff;"
  >
    <div class="text-center">
      <img class="text-center" src="@/assets/images/55444.png" alt />
    </div>
    <!-- <h3 class="text-center my-3">
      <b>{{ post.law_content_1 }}</b>
    </h3>
    <b>
      <p>{{ post.law_content_1 }}</p>
      <p>
        {{ post.law_content_2 ? post.law_content_2 : 'ความเห็นอื่นๆ (ถ้ามี)' }}
      </p>
      <p>
        {{ post.law_content_3 ? post.law_content_3 : 'ความเห็นอื่นๆ (ถ้ามี)' }}
      </p>
      <p>
        {{ post.law_content_4 ? post.law_content_4 : 'ความเห็นอื่นๆ (ถ้ามี)' }}
      </p>
      <p>ความเห็นอื่นๆ (ถ้ามี)</p>
    </b>-->
    <hr />
    <h4>ผู้สร้าง: {{ post.proposer_name }}</h4>
    <hr />
    <h4>
      ผู้สนับสนุน: {{ post.no_of_supporter }}
      คน
    </h4>
    <hr />
    <p class="text-left">
      <b>วันที่สร้าง</b>
      {{ new Date(post.proposed_date).toLocaleString() }}
    </p>
    <hr />
    <div v-if="isMember" class="ml-auto text-right">
      <div
        v-if="post.law_status === 3"
        class="text-right d-inline-block"
        style="cursor: pointer;"
      >
        <a
          class="hvr-buzz-out"
          title="ยอมรับร่างกฏหมาย"
          @click="showConfirmAccept(idcard, post.law_no)"
        >
          <v-btn class="bg-success text-white">
            <b style="font-size: 18px;"
              >ขอแจ้งความประสงค์ขอเข้าชื่อเสนอกฏหมายทางอิเลคโทนิค</b
            >
          </v-btn>
        </a>
      </div>
      <div
        v-if="
          post.law_status !== 12 &&
          post.law_status !== 14 &&
          post.law_status !== 3
        "
        class="text-right d-inline-block"
        style="cursor: pointer;"
      >
        <a
          class="hvr-buzz-out"
          title="โหวดเห็นด้วย"
          @click="showConfirm(idcard, post.law_no)"
        >
          <i
            class="far fa-check-circle"
            style="font-size: 50px; color: green;"
          ></i>
        </a>
      </div>
      <!-- <div
        v-if="
          post.law_status !== 12 &&
          post.law_status !== 14 &&
          post.law_status !== 4
        "
        class="text-right d-inline-block"
      >
        <a class="hvr-buzz-out">
          <i
            class="fas fa-times-circle"
            style="font-size: 50px; color: red;"
          ></i>
        </a>
      </div>-->
    </div>
    <div v-else v-app class="ml-auto text-right">
      <v-menu>
        <template v-slot:activator="{ on: menu, attrs }">
          <v-tooltip bottom>
            <template v-slot:activator="{ on: tooltip }">
              <v-btn
                color="primary"
                dark
                v-bind="attrs"
                v-on="{ ...tooltip, ...menu }"
                >ระบุ TimeLine</v-btn
              >
            </template>
            <span>ถึงขั้นตอนไหนแล้วนะ ?</span>
          </v-tooltip>
        </template>
        <v-list>
          <v-list-item v-for="(item, index) in items" :key="index" @click>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
      <div class="text-left">
        <input type="file" class="custom-file" name id />
      </div>
      <div class="text-right d-inline-block">
        <a
          class="hvr-buzz-out"
          title="อนุมัติ"
          @click="lawAcceptConfirm(post.law_no)"
        >
          <i
            class="far fa-check-circle"
            style="font-size: 50px; color: green;"
          ></i>
        </a>
      </div>
      <!-- <div class="text-right d-inline-block">
        <a class="hvr-buzz-out" @click="lawUnAcceptConfirm(post.law_no)">
          <i
            class="fas fa-times-circle"
            style="font-size: 50px; color: red;"
          ></i>
        </a>
      </div>-->
    </div>
    <hr />
    <div class="col-lg-12">
      <Timeline v-if="post.law_status < 4" :status="post.law_status" />
      <Timeline2 v-else :status="post.law_status" />
    </div>
    <!-- <div class="row">
      <div class="col-lg-6">
        <div
          class="alert alert-success col-lg-12 text-center mt-5"
          role="alert"
        >
          <h3 class="">
            <b>เข้าสู่ขั้นตอนที่ {{ post.law_status }}</b>
          </h3>
        </div>
      </div>
      <div class="col-lg-6">
        <p>
          <b>ขั้นตอนที่ 1</b> ผู้ริเริ่มเสนอกฏหมาย 20
          คนยื่นเรื่องพร้อมร่างกฏหมาย
        </p>
        <p><b>ขั้นตอนที่ 2</b> ตรวจสอบกฏหมาย ตาม หมวด 3 หมวด 5</p>
        <p><b>ขั้นตอนที่ 3</b> รอรายชื่อครบ 10000</p>
        <p><b>ขั้นตอนที่ 4</b> รอประธารรัฐสภาตรวจสอบภายใน 45 วัน</p>
        <p><b>ขั้นตอนที่ 5</b> บรรจุเข้าว่าละการประชุม</p>
      </div>
    </div>-->
  </div>
</template>

<script>
import Swal from 'sweetalert2'
import Timeline2 from '@/components/timeline2'
import Timeline from '@/components/timeline'
export default {
  components: {
    Timeline2,
    Timeline,
  },
  props: {
    post: { type: Object },
    isMember: { type: Boolean },
  },
  data() {
    return {
      idcard: '5555555',
      items: [
        { title: 'กำลังเข้าชื่อ' },
        { title: 'กำลังตรวจสอบ หมวด 3 และ 5' },
        { title: 'ตรวจสอบการใช้งบประมาณ' },
        { title: 'นายกพิจารณา' },
        { title: 'ประกาศตาม มาตรา 77' },
        { title: 'เข้าที่ประชุมสภา' },
      ],
    }
    // },
    // beforeMount() {
    //   if (localStorage.getItem('idcard') !== '') {
    //     this.idcard = localStorage.getItem('idcard')
    //   }
  },
  methods: {
    showConfirm(cardid, id) {
      Swal.fire({
        title: 'ร่วมส่งคำร้องใช่หรือไม่',
        // text: "You won't be able to revert this!",
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        cancelButtonText: 'ยกเลิก',
        confirmButtonText: 'ตกลง',
      }).then((result) => {
        console.log(result)
        if (result.value) {
          Swal.fire('Send!', 'Your request Successful', 'success')
          this.postAccept(cardid, id)
        }
      })
    },
    showConfirmAccept(cardid, id) {
      Swal.fire({
        title: 'ร่วมส่งคำร้องใช่หรือไม่',
        // text: "You won't be able to revert this!",
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        cancelButtonText: 'ยกเลิก',
        confirmButtonText: 'ตกลง',
      }).then((result) => {
        console.log(result)
        if (result.value) {
          Swal.fire('Send!', 'Your request Successful', 'success')
          this.gotoStatus(id)
        }
      })
    },
    async gotoStatus(id) {
      const res = await this.$axios.$post(`/fast_update`, {
        law_status: 4,
        law_no: id,
      })
      console.log(res)
      console.log(id)
    },
    async postAccept(cardid, id) {
      const res = await this.$axios.$post(`/law/${id}`, {
        supporter_idcard: cardid,
      })
      console.log(id)
    },
    lawAcceptConfirm(id) {
      Swal.fire({
        title: 'ยืนยันการอนุมัติ',
        showCancelButton: true,
      }).then((result) => {
        this.lawCheck(true, id, "35")
      })
    },
    lawUnAcceptConfirm(id) {
      Swal.fire({
        title: 'Enter your topic',
        input: 'text',
        showCancelButton: true,
        inputValidator: (value) => {
          if (!value) {
            return 'You need to write something!'
          } else {
            this.lawCheck(false, id, value)
          }
        },
      })
    },
    async lawCheck(approve, id, topic) {
      const res = await this.$axios.$post(`/approvement`, {
        approve,
        topic,
        process_by: 'admin',
        law_no: id,
      })
      console.log(res)
    },
  },
}
</script>

<style></style>
