<template>
  <div>
    <Carousel></Carousel>
    <div class="container-fluid">
      <div class="row">
        <div
          class="col-xl-2 col-lg-3 m-3 col-md-4 col-sm-6 mx-auto bg-gray shadow-sm border"
        >
          <div class="row">
            <div class="col-lg-12">
              <div class="p-5 h-100">
                <div class="text-center">
                  <img
                    class="rounded-circle mx-auto"
                    src="@/assets/images/1.jpg"
                    width="150px"
                    alt
                  />
                </div>
                <h5 class="text-center pt-2">ผู้ริเริ่มเสนอกฏหมาย</h5>
                <p class="text-white text-center">
                  (ผู้ริเริ่มเสนอกฏหมาย 20 คนยื่นเรื่องพร้อมร่างกฏหมาย)
                </p>
              </div>
            </div>
          </div>
        </div>
        <div
          class="col-xl-2 col-lg-3 m-3 col-md-4 col-sm-6 mx-auto shadow-sm border bg-gray"
        >
          <div class="row">
            <div class="col-lg-12">
              <div class="p-5 bg-gray h-100">
                <div class="text-center">
                  <img
                    class="rounded-circle mx-auto"
                    src="@/assets/images/2.jpg"
                    width="150px"
                    height="150px"
                    alt
                  />
                </div>
                <h5 class="text-center pt-2">
                  ผู้เข้าชื่อเสนอกฏหมาย (10,000 คน)
                </h5>
                <p class="text-white text-center">
                  รายชื่อผู้มีสิทธิเลือกตั้งครบ 10,000 รายชื่อ
                </p>
              </div>
            </div>
          </div>
        </div>
        <div
          class="col-xl-2 col-lg-3 m-3 col-md-4 col-sm-6 mx-auto shadow-sm border bg-gray"
        >
          <div class="row">
            <div class="col-lg-12">
              <div class="p-5 bg-gray h-100">
                <div class="text-center">
                  <img
                    class="rounded-circle mx-auto"
                    src="@/assets/images/3.jpg"
                    width="150px"
                    height="150px"
                    alt
                  />
                </div>
                <h5 class="text-center pt-2">ตรวจสอบสถานะ</h5>
                <p class="text-white text-center">
                  ตรวจสอบสถานะของกฎหมาย ว่าอยู่ในขั้นตอนการ ดำเนินงานใด
                </p>
              </div>
            </div>
          </div>
        </div>
        <div
          class="col-xl-2 col-lg-3 m-3 col-md-4 col-sm-6 mx-auto shadow-sm border bg-gray"
        >
          <div class="row">
            <div class="col-lg-12">
              <div class="p-5 bg-gray">
                <div class="text-center">
                  <img
                    class="rounded-circle mx-auto"
                    src="@/assets/images/4.png"
                    width="150px"
                    alt
                  />
                </div>
                <h5 class="text-center pt-2">ประกาศรายชื่อ</h5>
                <p class="text-white text-center">ประธานสภาประกาศรายชื่อ</p>
                <p class="text-white m-0">1. ทาง Internet</p>
                <p class="text-white m-0">2. จัดให้มาตรวจสอบได้</p>
                <p class="text-white m-0">
                  3. แจ้งไปยังคนที่มีรายชื่อ เพื่อให้ประชาชนคัดค้านได้
                </p>
              </div>
            </div>
          </div>
        </div>
        <div
          class="col-xl-2 col-lg-3 m-3 col-md-4 col-sm-6 mx-auto shadow-sm border bg-gray"
        >
          <div class="row">
            <div class="col-lg-12">
              <div class="p-5 bg-gray h-100">
                <div class="text-center">
                  <img
                    class="rounded-circle mx-auto"
                    src="@/assets/images/5.jpg"
                    width="150px"
                    height="150px"
                    alt
                  />
                </div>
                <h5 class="text-center pt-2">
                  กฎหมายที่เกี่ยวข้อง และสาระน่ารู้
                </h5>
                <p class="text-white text-center">ความรู้เรื่องกฏหมาย</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="container-fluid my-5">
      <div class="row p-4 bg-gray">
        <div class="col-lg-6">
          <ContentInitLaw v-if="post != null" :post="post" :isMember="true" />
          <div v-else class="col-lg-6" style="background-color: #ffffff;"></div>
        </div>
        <div class="col-lg-6 px-5 mx-auto">
          <div class="col-lg-12 mt-3">
            <h5>
              <b>ข้อเสนอที่แนะนำ</b>
            </h5>
            <p>ข้อเสนอที่มีคนสนับสนุนมากที่สุด</p>
          </div>
          <div class="row">
            <CardInitLaw
              v-for="(law, i) in laws"
              :key="law.law_no"
              :law="law"
              :index="i"
              @clickCardInitLaw="getPost"
            />
          </div>
          <div class="col-lg-12">
            <nuxt-link class="text-center text-decoration-none" to="/posts"
              ><p class="bg-white py-3 rounded-pill">
                ดูการร่างกฏหมายของผู้เสนอทั้งหมด
              </p></nuxt-link
            >
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Carousel from '@/components/carousel'
import CardInitLaw from '@/components/cardInitLaw'
import ContentInitLaw from '@/components/contentInitLaw'
export default {
  components: {
    Carousel,
    CardInitLaw,
    ContentInitLaw,
  },
  async asyncData({ $axios }) {
    const res = await $axios.$get('/law')
    const data = res.data.filter(
      (law) =>
        law.law_status === 1 ||
        law.law_status === 2 ||
        law.law_status === 3 ||
        law.law_status === 4
    )
    return {
      laws: data,
      post: data[0],
    }
  },
  data() {
    return {
      laws: [],
      post: null,
    }
  },
  // mounted() {
  //   this.getAllType1000Law()
  // },
  methods: {
    // async getAllType1000Law() {
    //   const res = await this.$axios.$get('/law?type=10000')
    //   this.laws = res.data
    //   this.post = res.data[0]
    //   console.log(this.laws)
    // },
    async getPost(id) {
      const res = await this.$axios.$get(`/law/${id}`)
      this.post = res.data
      console.log(res.data)
    },
  },
}
</script>

<style></style>
