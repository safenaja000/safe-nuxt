<template>
  <div class="row p-4 bg-gray">
    <div class="col-lg-6">
      <div class="row">
        <ContentInitLaw v-if="post != null" :post="post" :isMember="false" />
        <div
          v-else
          class="col-lg-12"
          style="background-color: #ffffff; height: 100px;"
        >
          <h1 class="text-center">เลือกคำร้องที่ต้องการ</h1>
        </div>
      </div>
    </div>
    <div class="col-lg-6 px-5 mx-auto">
      <div class="row">
        <!-- <h3 class="text-center col-lg-8">ผู้ที่อยู่ในขั้นตอน ที่ 2</h3> -->
        <div class="col-lg-12 ml-auto">
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
            <template v-slot:item.approve="{ item }">
              <v-btn color="success" @click="getPost(item)">ตรวจสอบ</v-btn>
            </template>
          </v-data-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ContentInitLaw from '@/components/contentInitLaw'
export default {
  components: {
    ContentInitLaw,
  },
  layout: 'admin',
  async asyncData({ $axios }) {
    const res = await $axios.$get('/law?type=draft')
    return {
      laws: res.data, // .filter((law) => law.law_status > 1),
    }
  },
  data() {
    return {
      headers: [
        { text: 'หัวข้อ', value: 'law_content_1', align: 'center' },
        { text: 'ผู้ริเริ่ม', value: 'proposer_name', align: 'left' },
        { text: 'เวลาที่สร้าง', value: 'proposed_date', align: 'center' },
        { text: 'จำนวน', value: 'no_of_supporter', align: 'center' },
        { text: 'ตรวจสอบ', value: 'approve', align: 'center' },
      ],
      laws: [],
      search: '',
      post: null,
    }
  },
  methods: {
    async getPost(item) {
      const res = await this.$axios.$get(`/law/${item.law_no}`)
      this.post = res.data
      console.log(this.post)
    },
  },
}
</script>

<style></style>
