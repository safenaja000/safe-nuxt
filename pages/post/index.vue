<template>
  <div>
    <div class="container-fluid my-5">
      <div class="row p-4 bg-gray">
        <div class="col-lg-6">
          <ContentInitLaw v-if="post != null" :post="post" :isMember="true" />
          <div v-else class="col-lg-6" style="background-color: #ffffff;"></div>
        </div>
        <div class="col-lg-6 px-5 mx-auto">
          <div
            class="col-lg-12 p-3 bg-white shadow-sm rounded mb-3 hvr-bounce-out"
          >
            <nuxt-link to="/addpost" class="text-decoration-none" href>
              <h1 class="text-center text-dark m-4">+ สร้างข้อเสนอ</h1>
            </nuxt-link>
          </div>
          <div class="row">
            <CardInitLaw
              v-for="(law, i) in laws"
              :key="law.law_no"
              :law="law"
              :index="i"
              @clickCardInitLaw="getPost"
            />
            <!-- <v-pagination v-model="page" :length="length"></v-pagination> -->
          </div>
          <div class="col-lg-12">
            <nuxt-link class="text-center text-decoration-none" to="/posts"
              ><p class="bg-white py-3 rounded-pill">
                ดูการร่างกฏหมายของผู้เสนอทั้งหมด
              </p>
            </nuxt-link>
          </div>
        </div>
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
  async asyncData({ $axios }) {
    const res = await $axios.$get('/law?type=1')
    return {
      laws: res.data,
      post: res.data[0],
    }
  },
  data() {
    return {
      post: null,
      laws: [],
      page: 1,
      length: 6,
    }
  },
  // mounted() {
  //   this.getInitLaw()
  //   // this.length = this.laws.length / 3
  // },
  methods: {
    async getPost(id) {
      const res = await this.$axios.$get(`/law/${id}`)
      this.post = res.data
      console.log(res.data)
    },
    // async getInitLaw() {
    //   const res = await this.$axios.$get('/law?type=20')
    //   this.laws = res.data
    //   this.post = res.data[0]
    //   console.log(res.data)
    // },
  },
}
</script>

<style></style>
