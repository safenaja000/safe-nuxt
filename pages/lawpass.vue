<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-4 ml-auto">
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </div>
      <div class="col-lg-12">
        <v-data-table
          :headers="headers"
          class="elevation-1"
          :items="laws"
          :search="search"
        >
          <template v-slot:item.proposed_date="{ item }">
            <span>{{ new Date(item.proposed_date).toLocaleString() }}</span>
          </template>
          <template v-slot:item.law_status="{ item }">
            <span class="text-success">{{
              item.law_status == 5 ? 'เตรียมเข้าการประชุม' : 'Error'
            }}</span>
          </template>
          <template v-slot:item.check="{ item }">
            <v-btn color="#64B5F6" @click="getPost(item)">ตรวจสอบ</v-btn>
          </template>
        </v-data-table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    const res = await $axios.$get('/law?type=5')
    return {
      laws: res.data,
    }
  },
  data() {
    return {
      laws: [],
      search: '',
      headers: [
        { text: 'หัวข้อ', value: 'law_content_1', align: 'center' },
        { text: 'ผู้ริเริ่ม', value: 'proposer_name', align: 'left' },
        { text: 'เวลาที่สร้าง', value: 'proposed_date', align: 'center' },
        { text: 'จำนวน', value: 'no_of_supporter', align: 'center' },
        { text: 'อยู่ในขั้นตอนที่', value: 'law_status', align: 'center' },
        { text: 'ตรวจสอบ', value: 'check', align: 'center' },
      ],
    }
  },
  methods: {
    getPost(object) {
      // console.log(object)
      this.$router.push(`/post/${object.law_no}`)
    },
  },
}
</script>

<style></style>
