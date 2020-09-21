<template>
  <div>
    <v-timeline
      v-if="
        status == 1 || status == 2 || status == 3 || status == 4 || status == 5
      "
      :dense="true"
    >
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 4 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>ขั้นตอนที่ 1</b> กำลังเข้าชื่อ
            </p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 5 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>ขั้นตอนที่ 2</b> กำลังตรวจสอบ หมวด 3 และ 5 ตาม หมวด 3 หมวด 5</p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 6 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>ขั้นตอนที่ 3</b>วินิฉัยการเงิน</p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <!-- <v-timeline-item
        :small="true"
        right="right"
        :color="status == 7 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>ขั้นตอนที่ 4</b>นายกพิจารณา</p>
          </v-card-title>
        </v-card>
      </v-timeline-item> -->
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 8 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>ขั้นตอนที่ 4</b>รับฟังความคิดเห็น ตามมาตรา 77</p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
    </v-timeline>

    <v-timeline v-else :dense="true">
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 9 ? '#FF0000' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>บรรจุระเบียบวาระ</b>
            </p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 13 ? '#FF0000' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>ถูกตัดออกเพราะมีการใช้สิทธิไม่ถูกต้อง</b>
            </p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 14 ? '#FF0000' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>ประธานรัฐสภา ไม่อนุมัติ</b>
            </p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
    </v-timeline>
  </div>
</template>

<script>
export default {
  props: {
    status: Number,
  },
  data() {
    return {}
  },
}
</script>

<style></style>
