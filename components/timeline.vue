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
        :color="status == 1 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>รวบรวมรายชื่อ จัดทำร่างกฏหมาย</b>
            </p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 2 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>อยู่ในขั้นตอนจัดทำร่าง</b></p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 3 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>จัดทำร่างกฏหมายเสร็จสิ้น</b></p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 4 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>เริ่มเข้าชื่อเสนอกฏหมาย</b></p>
          </v-card-title>
        </v-card>
      </v-timeline-item>
      <!-- <v-timeline-item
        :small="true"
        right="right"
        :color="status == 5 ? '#28a745' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p><b>ขั้นตอนที่ 5</b> บรรจุเข้าว่าละการประชุม</p>
          </v-card-title>
        </v-card>
      </v-timeline-item> -->
    </v-timeline>

    <v-timeline v-else :dense="true">
      <v-timeline-item
        :small="true"
        right="right"
        :color="status == 12 ? '#FF0000' : '#e4e4e4'"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline">
            <p>
              <b>ไม่ผ่านอารอนุมัติ หมวด 3 หมวด 5</b>
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
