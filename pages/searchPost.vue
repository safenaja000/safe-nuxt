<template>
  <div>
    <div class="container">
      <div class="row">
        <v-col class="mx-auto" cols="12" sm="6" md="4">
          <v-text-field
            label="หัวข้อที่ท่านต้องการค้นหา"
            filled
            dense
            @input="searchLaws"
          ></v-text-field>
        </v-col>
      </div>
      <div class="row bg-gray">
        <CardInitLaw
          v-for="(law, i) in laws"
          :key="law.law_no"
          :index="i"
          :law="law"
          :isMember="true"
          @clickCardInitLaw="getPost"
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
    const res = await $axios.$get('/law')
    return {
      laws: res.data,
    }
  },
  data() {
    return {
      search: '',
      laws: [],
    }
  },
  methods: {
    async searchLaws() {
      const res = await this.$axios.$get('/law/search')
      this.laws = res.data
    },
    getPost(lawId) {
      this.$router.push(`/post/${lawId}`)
    },
  },
}
</script>

<style></style>
