<template>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-lg-6">{{ user.member_id }}</div>
        <div class="col-lg-6"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {},
    }
  },
  methods: {
    async getUserData() {
      const res = await this.$axios.$get('member/1349900965669')
      this.user = res.data
      console.log(res.data)
    },
  },
  mounted() {
    this.getUserData()
  },
}
</script>

<style></style>
