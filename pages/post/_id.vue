<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12 shadow-sm bg-gray">
        <ContentInitLaw v-if="post != null" :post="post" :isMember="true" />
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
  data() {
    return {
      post: null,
    }
  },
  created() {
    this.getPost(this.$route.params.id)
  },
  methods: {
    async getPost(id) {
      const res = await this.$axios.$get(`/law/${id}`)
      this.post = res.data
    },
  },
}
</script>

<style></style>
