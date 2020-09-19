<template>
  <div class="container">
    <div class="row">
      <div class="col-lg-12">
        <h1>sasas</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'admin',
  async asyncData({ $axios }) {
    const res = await $axios.get('/user')
    return {
      users: res.data,
    }
  },
  data() {
    return {
      users: null,
    }
  },
  methods: {
    ConfirmUser(id) {
      console.log(id)
    },
  },
}
</script>

<style></style>
