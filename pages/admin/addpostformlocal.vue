<template>
  <div class="container">
    <v-text-field
      v-model="law_content_1"
      label="รหัสยืนยันกฏหมาย"
      required
    ></v-text-field>
    <v-textarea
      v-model="law_content_2"
      solo
      label="เลขบัตรประชาชน"
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
