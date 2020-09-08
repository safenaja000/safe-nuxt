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
    <v-btn x-large color="success" dark @click="showConfirm()"
      >ยืนยันการร่างกฏหมาย</v-btn
    >
  </div>
</template>

<script>
import Swal from 'sweetalert2'
import 'sweetalert2/src/sweetalert2.scss'
export default {
  data() {
    return {
      law_content_1: '',
      law_content_2: '',
      law_content_3: '',
      law_content_4: '',
    }
  },
  methods: {
    showConfirm() {
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
          Swal.fire('Send!', 'Send your law Successful', 'success')
          this.setLaw()
        }
      })
    },
    async setLaw() {
      const res = await this.$axios.$post('/law', {
        law_content_1: this.law_content_1,
        law_content_2: this.law_content_2,
        law_content_3: this.law_content_3,
        law_content_4: this.law_content_4,
        proposer_idcard: 1349900965669,
      })
      console.log(res)
    },
  },
}
</script>

<style></style>
