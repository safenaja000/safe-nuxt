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
          <h1 class="text-center">เลือก ร่างกฏหมาย ที่จะ อนุมัติ/ไม่อนุมัติ</h1>
        </div>
      </div>
    </div>
    <div class="col-lg-6 px-5 mx-auto">
      <div class="row">
        <h3>ผู้ที่อยู่ในขั้นตอน ที่ 2</h3>
        <CardInitLaw
          v-for="(law, i) in laws"
          :key="law.law_no"
          :law="law"
          :index="i"
          @clickCardInitLaw="getPost"
          :isMember="false"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CardInitLaw from '@/components/cardInitLaw'
import ContentInitLaw from '@/components/contentInitLaw'
export default {
  components: {
    CardInitLaw,
    ContentInitLaw,
  },
  layout: 'admin',
  async asyncData({ $axios }) {
    const res = await $axios.$get('/law?type=3')
    return {
      laws: res.data, // .filter((law) => law.law_status > 1),
    }
  },
  data() {
    return {
      laws: [],
      post: null,
    }
  },
  methods: {
    async getPost(id) {
      const res = await this.$axios.$get(`/law/${id}`)
      this.post = res.data
      console.log(res)
    },
  },
}
</script>

<style></style>
