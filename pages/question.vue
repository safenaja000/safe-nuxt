<template>
  <div>
    <Carousel />
    <div class="container">
      <div class="row">
        <p
          class="col-lg-12 font-18"
        >Q:สามารถยื่นคำขอไปสำนักงานเลขาธิการสภาผู้แทนราษฎรช่วยยกร่างกฎหมายได้หรือไม่อย่างไร</p>
        <p
          class="col-lg-12 font-18"
        >A:สามารถยื่นคำร้องขอไปทางสำนักงานเลขาธิการสภาผู้แทนราษฎรช่วยยกร่างกฎหมายได้โดยต้องมีผู้ริเริ่ม จำนวน 20 คน ยื่นคำร้องขอต่อสำนักงาน</p>
        <p class="col-lg-12 font-18">Q:ผู้มีสิทธิร่วมเข้าชื่อเสนอกฎหมายต้องมีคุณสมบัติอย่างไร</p>
        <p class="col-lg-12 font-18">A:ต้องเป็นสิทธิผู้เลือกตั้งตามรัฐธรรมนูญ</p>
        <p class="col-lg-12 font-18">Q:ร่างกฎหมายต้องประกาศผลประกอบด้วยอะไรบ้าง</p>
        <p class="col-lg-12 font-18">
          A:ร่างกฎหมายต้องประกอบด้วย
          1.หลักการและเหตุผลของร่าง
          2.ตัวร่างพระราชบัญญัติ
          3.สรุปสาระสำคัญร่าง
        </p>
        <div class="col-lg-12">
          <v-text-field
          class="col-4"
            value="Email"
            label="Solo"
            solo
            disabled
          ></v-text-field>
          <v-text-field
          class="col-4"
            value="ชื่อ-สกุล"
            label="Solo"
            solo
            disabled
          ></v-text-field>
          <v-textarea solo name="input-7-4" label="แสดงความคิดเห็น"></v-textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Carousel from '@/components/carousel'
export default {
  components: {
    Carousel,
  },
}
</script>

<style>
.font-18{
  font-size:'18px'
}
</style>
