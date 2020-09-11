<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <div class="text-center">
          <img :src="url" width="460px" alt />
        </div>
        <form id="form" @submit.prevent="submit"
          action="http://e-init-ay.herokuapp.com/api/identify"
          method="post"
          enctype="multipart/form-data"
        >
          <input class="form-control" type="text" readonly name="id_card" value="1349900965669" />
          <v-text-field label="Laser ID" name="laser_id" single-line></v-text-field>
          <input class="mb-3" type="file" name="file" @change="onFileChange" />
          <br />
          <v-btn class="bg-success" style="font-size: 1.5rem;" type="submit">ยืนยันตัวตน</v-btn>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      url: null,
    }
  },
  methods: {
    onFileChange(e) {
      const file = e.target.files[0]
      this.url = URL.createObjectURL(file)
    },
    submit(e) {
      var form = document.getElementById('form')
      var formData = new FormData(form)

      this.$axios.$post('/identify', formData).then(
        (response) => {
          this.url = response.img_url
          console.log(response)
        },
        (response) => {
          // error callback
        }
      )
    },
  },
}
</script>

<style></style>
