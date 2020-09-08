<template>
  <div class="container">
    <div class="container-fluid my-5">
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
          <v-data-table :headers="headers" class="elevation-1" :items="users" :search="search" >
            <template v-slot:item.edit="{item}">
              <v-btn color="success">Approve</v-btn>
            </template>
          </v-data-table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'admin',
  data() {
    return {
      headers: [
        { text: 'id', value: 'id', align: 'center',width:'1em' },
        { text: 'name', value: 'name', align: 'left',width:'3em' },
        { text: 'email', value: 'email', align: 'center',width:'3em' },
        { text: 'Edit', value: 'edit', align: 'center',width:'2em' },
      ],
      users: [],
      search: '',
    }
  },
  mounted() {
    this.getAllUsers()
  },
  methods: {
    async getAllUsers() {
      const res = await this.$axios.get(
        'https://jsonplaceholder.typicode.com/users'
      )
      this.users = res.data
      console.log(res.data)
    },
    clicked(all) {
      console.log(all)
    },
  },
}
</script>

<style></style>
