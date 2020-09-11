<template>
  <div class="container">
    <v-text-field
      v-model="law_content_1"
      label="หัวข้อร่างกฏหมาย"
      required
    ></v-text-field>
    <v-textarea
      v-model="law_content_2"
      solo
      label="หลักการของกฏหมาย"
    ></v-textarea>
    <v-textarea
      v-model="law_content_3"
      solo
      label="ความสำคัญของกฏหมาย"
    ></v-textarea>
    <v-textarea
      v-model="law_content_4"
      solo
      label="เหตุผลในการร่างกฏหมาย"
    ></v-textarea>
    <v-btn x-large color="success" dark @click=""
      >ยืนยันการร่างกฏหมาย</v-btn
    >
  </div>
</template>

<script>
export default {
layout: 'admin',
}
</script>

<style>

</style>
