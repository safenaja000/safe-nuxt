<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-6 mx-auto bg-gray">
        <h1 class="text-center">กฏหมายอยู่ในขั้นตอนที่ 1</h1>
        <CardInitLaw
          v-for="(law, i) in laws20"
          :key="law.law_no"
          :law="law"
          :index="i"
          @clickCardInitLaw="getPost(law.law_no)"
        />
      </div>
      <div class="col-lg-6 mx-auto bg-gray">
        <h1 class="text-center">กฏหมายอยู่ในขั้นตอนที่ 3</h1>
        <CardInitLaw
          v-for="(law, i) in laws10000"
          :key="law.law_no"
          :law="law"
          :index="i"
          @clickCardInitLaw="getPost(law.law_no)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CardInitLaw from '@/components/cardInitLaw'
export default {
  components: {
    CardInitLaw,
  },
  async asyncData({ $axios }) {
    const res1 = await $axios.$get('law?type=1')
    const res3 = await $axios.$get('law?type=3')
    return {
      laws20: res1.data,
      laws10000: res3.data,
    }
  },
  data() {
    return {
      laws20: [],
      laws10000: [],
    }
  },
  methods: {
    getPost(lawId) {
      this.$router.push(`/post/${lawId}`)
    },
  },
}
</script>

<style></style>
