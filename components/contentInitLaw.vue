<template>
  <div
    v-if="post != null"
    class="col-lg-6 rounded"
    style="background-color: #ffffff;"
  >
    <h3 class="text-center my-3">
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
    </b>
    <hr />
    <h4>ผู้สร้าง: {{ post.proposer_name }}</h4>
    <hr />
    <h4>
      ผู้สนับสนุน: {{ post.no_of_supporter }}/{{
        post.law_status == 3 ? 10000 : 20
      }}
      คน
    </h4>
    <hr />
    <p class="text-left">
      <b>วันที่สร้าง</b>
      {{ post.proposed_date }}
    </p>
    <hr />
    <div class="ml-auto text-right">
      <div class="text-right d-inline-block">
        <a class>
          <img
            src="@/assets/images/accept.png"
            width="50px"
            alt
            style="cursor: pointer;"
            @click="showConfirm(idcard, post.law_no)"
          />
        </a>
      </div>
      <div class="text-right d-inline-block">
        <a class>
          <img src="@/assets/images/unaccept.png" width="50px" alt />
        </a>
      </div>
    </div>
    <hr />
    <div class="col-lg-10 ml-auto">
      <Timeline :status="post.law_status" />
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
import Timeline from '@/components/timeline'
export default {
  data() {
    return {
      idcard: '',
    }
  },
  beforeMount() {
    if (localStorage.getItem('idcard') !== '') {
      this.idcard = localStorage.getItem('idcard')
    }
  },
  components: {
    Timeline,
  },
  props: {
    post: Object,
  },
  methods: {
    showConfirm(cardid, id) {
      Swal.fire({
        title: 'Are you sure?',
        text: "You won't be able to revert this!",
        icon: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#3085d6',
        cancelButtonColor: '#d33',
        confirmButtonText: 'Yes, Send it!',
      }).then((result) => {
        if (result.value) {
          Swal.fire('Send!', 'Your request Successful', 'success')
          this.postAccept(cardid, id)
        }
      })
    },
    async postAccept(cardid, id) {
      const res = await this.$axios.$post(`/law/${id}`, {
        supporter_idcard: cardid,
      })
      console.log(res)
    },
  },
}
</script>

<style></style>
